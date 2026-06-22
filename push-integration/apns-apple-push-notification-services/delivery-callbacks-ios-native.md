# Delivery callbacks (iOS Native)

Each notification triggered through Sortment carries a `callback` URL in its data payload. To track delivery and interaction, your app reads that URL and sends a `POST` request with the relevant status (`RECEIVED` or `CLICKED`) back to it.

On a native iOS app this is wired up in two places:

* A **Notification Service Extension** reports `RECEIVED` whenever a notification is delivered, in every app state.
* Your **`AppDelegate`** reports `CLICKED` when the user taps a notification.

***

**Setup: register the notification delegate**

Set your `AppDelegate` as the notification center delegate when the app launches. Without this, the tap callback will not fire.

```swift
import UIKit
import UserNotifications
import FirebaseCore

@main
class AppDelegate: UIResponder, UIApplicationDelegate, UNUserNotificationCenterDelegate {

    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
    ) -> Bool {
        FirebaseApp.configure()
        UNUserNotificationCenter.current().delegate = self
        application.registerForRemoteNotifications()
        return true
    }
}
```

***

**1. Notification Delivered (`RECEIVED`)**

Delivery is tracked with a Notification Service Extension. It runs in its own process, launched by the system before the notification is displayed, so it reports delivery in every app state: foreground, background, and closed (including force-quit).

**Step 1: Add the extension target**

In Xcode, go to **File → New → Target**, select **Notification Service Extension**, give it a name (for example, `NotificationReceiptService`), choose **Swift**, and click **Finish**. If prompted to activate the scheme, click **Cancel**.

Make sure the extension's **deployment target** is the same as or lower than your main app's.

**Step 2: Add the receipt logic**

Open the generated `NotificationService.swift` and replace its contents with the following.

```swift
import UserNotifications

class NotificationService: UNNotificationServiceExtension {

    private var contentHandler: ((UNNotificationContent) -> Void)?
    private var bestAttemptContent: UNMutableNotificationContent?

    override func didReceive(
        _ request: UNNotificationRequest,
        withContentHandler contentHandler: @escaping (UNNotificationContent) -> Void
    ) {
        self.contentHandler = contentHandler
        self.bestAttemptContent = request.content.mutableCopy() as? UNMutableNotificationContent

        let userInfo = request.content.userInfo

        // Extract the callback URL from the data payload
        guard
            let callbackUrlString = userInfo["callback"] as? String,
            let callbackUrl = URL(string: callbackUrlString)
        else {
            deliver()
            return
        }

        var receipt = URLRequest(url: callbackUrl)
        receipt.httpMethod = "POST"
        receipt.setValue("application/json", forHTTPHeaderField: "Content-Type")
        receipt.httpBody = try? JSONSerialization.data(withJSONObject: ["status": "RECEIVED"])

        // Send the receipt, then deliver the notification once it completes
        URLSession.shared.dataTask(with: receipt) { [weak self] _, _, error in
            if let error = error {
                print("[FCM] Failed to send RECEIVED callback: \(error)")
            }
            self?.deliver()
        }.resume()
    }

    /// Hands the notification to the system for display.
    private func deliver() {
        if let contentHandler = contentHandler, let bestAttemptContent = bestAttemptContent {
            contentHandler(bestAttemptContent)
        }
    }

    /// Safety net: the system calls this just before terminating the extension.
    /// Deliver the notification anyway so it is never lost waiting on the network.
    override func serviceExtensionTimeWillExpire() {
        deliver()
    }
}
```

The extension has roughly a 30-second window. The notification is displayed as soon as the receipt request returns, and `serviceExtensionTimeWillExpire()` ensures it still shows even if the network is slow.

***

**2. Notification Clicked (`CLICKED`)**

When the user taps a notification to open the app, from either the background or a closed state, iOS routes both cases through `userNotificationCenter(_:didReceive:withCompletionHandler:)`. Add this method to your `AppDelegate`.

```swift
extension AppDelegate {

    func userNotificationCenter(
        _ center: UNUserNotificationCenter,
        didReceive response: UNNotificationResponse,
        withCompletionHandler completionHandler: @escaping () -> Void
    ) {
        let userInfo = response.notification.request.content.userInfo
        sendClickedStatus(userInfo: userInfo)
        completionHandler()
    }

    /// Sends the CLICKED status to the callback URL from the notification payload.
    private func sendClickedStatus(userInfo: [AnyHashable: Any]) {
        guard
            let callbackUrlString = userInfo["callback"] as? String,
            let callbackUrl = URL(string: callbackUrlString)
        else {
            return
        }

        var request = URLRequest(url: callbackUrl)
        request.httpMethod = "POST"
        request.setValue("application/json", forHTTPHeaderField: "Content-Type")
        request.httpBody = try? JSONSerialization.data(withJSONObject: ["status": "CLICKED"])

        URLSession.shared.dataTask(with: request) { _, _, error in
            if let error = error {
                print("[FCM] Failed to send CLICKED callback: \(error)")
            }
        }.resume()
    }
}
```
