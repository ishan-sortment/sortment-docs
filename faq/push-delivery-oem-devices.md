# Push Delivery on Oppo, Vivo, OnePlus & Xiaomi Devices

A common question during onboarding: *"CleverTap and MoEngage advertise OEM-specific push capabilities for Chinese-brand Android devices. Does Sortment support Oppo, Vivo, OnePlus, and Xiaomi phones?"*

**Short answer: yes — through Firebase Cloud Messaging (FCM), which is the native system push channel on every one of these devices sold outside mainland China. No OEM-specific SDK or partnership is required, and here's why.**

## Outside China, FCM *is* the OEM channel

Oppo, Vivo, OnePlus, and Xiaomi devices sold in India and other global markets ship with Google Mobile Services. FCM is their system-level push service — the same one Google's own apps use. The proprietary OEM push SDKs (Oppo Push, Vivo Push, Mi Push) exist for **mainland China**, where Google services are blocked. Infrastructure providers like [Alibaba Cloud document this split explicitly](https://www.alibabacloud.com/help/en/mobile-platform-as-a-service/latest/channel-configuration): OEM vendor channels inside mainland China, FCM outside.

The clearest evidence comes from Xiaomi itself — historically the most aggressive OS for background restrictions. In March 2024, Xiaomi **discontinued Mi Push for all markets outside mainland China** and directed developers to FCM. [CleverTap](https://developer.clevertap.com/docs/discontinuation-of-xiaomi-push-service) and [MoEngage](https://help.moengage.com/hc/en-us/articles/23072207451540-Discontinuation-of-Mi-Push-Service) both published migration notes moving Xiaomi devices back to FCM — with MoEngage noting Mi Push had offered only *"marginally better delivery rates over FCM."*

The "standard push APIs" these OEMs collaborated on — the [Unified Push Alliance](https://www.yicaiglobal.com/news/china-forms-unified-push-alliance-to-optimize-notifications-on-android-devices) — is a China-only initiative directed by China's MIIT, solving a China-only problem. It has no bearing on devices running Google Mobile Services.

This is also why globally-focused platforms like **Braze** and **Iterable** send Android push through FCM without OEM-specific channels — it's the standard, not a workaround.

## Then what is "Push Amplification" / "RenderMax"?

The real challenge on these devices was never the delivery channel — it's **aggressive battery optimization**. ColorOS, OxygenOS, and MIUI/HyperOS kill background processes, which can suppress notification *rendering* even after FCM delivers the message.

Products like [MoEngage Push Amplification](https://help.moengage.com/hc/en-us/articles/360039754532-Push-Amplification-Plus-and-Delivery-Impact) and [CleverTap RenderMax](https://docs.clevertap.com/docs/rendermax) address this with SDK-side engineering, not OEM business deals: detecting the device's battery-optimization state, sending high-priority payloads, and polling their servers as a fallback for missed notifications. The OEM-partnership framing in their marketing primarily concerns Huawei and Baidu — relevant for devices without Google services, not for the Oppo/Vivo/OnePlus phones in your user base.

## How Sortment delivers the same outcome

**1. High-priority FCM delivery.** [Google's own guidance](https://firebase.blog/posts/2025/04/fcm-on-android/) is that high-priority FCM messages wake a device even in Doze mode and are the correct mechanism for user-visible notifications. Sortment sends campaign pushes accordingly through your own Firebase project — set up in minutes via [the FCM integration](https://docs.sortment.com/push-integration/google-fcm).

**2. Delivery and interaction callbacks.** Sortment's [FCM integration](https://docs.sortment.com/push-integration/google-fcm) includes `RECEIVED` and `CLICKED` callbacks, so [campaign reports](https://docs.sortment.com/engage/campaigns/campaign-reports) show what actually rendered and got engagement on-device — not just what was handed to FCM. You measure the render gap instead of guessing at it.

**3. Cross-channel fallback via Journeys.** Because Sortment runs on your warehouse, the durable answer to any single channel's delivery ceiling is orchestration, not a proprietary side-channel. In [Journeys](https://docs.sortment.com/journeys), use [flow control and delays](https://docs.sortment.com/journeys/journey-components) to branch on engagement — e.g., *if push not clicked within 6 hours → send WhatsApp or SMS*. The user is reached either way, on channels with delivery guarantees no Android OEM can interfere with.

## Automations to set up during onboarding

* **[FCM + APNs sender profiles](https://docs.sortment.com/push-integration/google-fcm)** — connect your Firebase project and [APNs](https://docs.sortment.com/push-integration/apns-apple-push-notification-services) keys, and implement the delivery callbacks in your app.
* **[Push → WhatsApp/SMS fallback journey](https://docs.sortment.com/journeys/tutorial-creating-a-journey)** — a reusable journey pattern that re-targets push non-engagers on a second channel.
* **[Delivery controls](https://docs.sortment.com/settings/delivery-controls)** — quiet hours, frequency caps, and suppression rules so the fallback logic never over-messages anyone.
* **[Alerts](https://docs.sortment.com/settings/alerts)** — get notified when a campaign's delivery metrics deviate, so channel-level issues surface immediately.
* **[Test profiles](https://docs.sortment.com/settings/test-profiles)** — before going live, test push rendering on your team's actual Oppo/Vivo/OnePlus devices, including in battery-optimized states.

{% hint style="info" %}
**The one exception:** if you target users **inside mainland China**, OEM push channels genuinely matter there, since those devices lack Google services. For India and other global markets, FCM is the native and complete answer.
{% endhint %}

## References

* [Firebase: Ensure your FCM notifications reach your users on Android](https://firebase.blog/posts/2025/04/fcm-on-android/)
* [CleverTap: Discontinuation of Xiaomi Push Service](https://developer.clevertap.com/docs/discontinuation-of-xiaomi-push-service)
* [MoEngage: Discontinuation of Mi Push Service](https://help.moengage.com/hc/en-us/articles/23072207451540-Discontinuation-of-Mi-Push-Service)
* [Alibaba Cloud: Push channel configuration in/outside mainland China](https://www.alibabacloud.com/help/en/mobile-platform-as-a-service/latest/channel-configuration)
* [Yicai Global: China forms Unified Push Alliance](https://www.yicaiglobal.com/news/china-forms-unified-push-alliance-to-optimize-notifications-on-android-devices)
* [CleverTap: Why push notifications go undelivered on Android](https://clevertap.com/blog/why-push-notifications-go-undelivered-and-what-to-do-about-it/)
