# Google FCM

Before integrating FCM with Sortment, you will need to have an account already set up in FCM with an App built (SDK) within FCM.

**Step 1: Find the Provider**

Navigate to **Workspace Settings → Sender Profiles**. Under the "Add integration" section, click on the **FCM** button.

**Step 2: Configure the Integration**

In the pop-up that appears, fill in:

* **Custom name:** Provide a name that would help you identify the configured account in Sortment's portal.
* **Firebase Project ID:** Log into your Firebase (FCM) panel and find the app that you would like to connect to.
  1. On the "Project Overview" tab on the left navigation panel, find the "Settings" icon and select "Project Settings".
  2. On the page that opens, find "Service Accounts" on the ribbon menu and click on [Generate New Private Key](https://firebase.google.com/docs/admin/setup?authuser=0#initialize-sdk). If you are not able to see "Generate New Private Key", you will need to first "Create a new Service Account" by clicking on the button.
  3. Once downloaded, open the file, which will contain the `project_id`. Fill in the details.
* **Private Key:** Following the same steps as above, you can find the "Private Key" in the downloaded file.
* **Client Email:** Following the same steps as above, you can find the "Client Email" in the downloaded file.

**Step 3: Complete the Integration**

Click on **Add Account** once done and you are all set!

> **Important — "Private Key" format matters!** When you copy the "Private Key" from the downloaded file, copy the entire value within the quotes, including the prefix and suffix as below: `-----BEGIN PRIVATE KEY-----your_key-----END PRIVATE KEY-----`

#### Message Delivery Status

**1. Foreground Delivery Callback (`RECEIVED`)**

To track when a notification is successfully delivered while the app is in the foreground, you must listen to the `messaging().onMessage` stream.

Add the following logic inside your top-level component (e.g., `App.tsx` or a dedicated Notification Manager context):

typescript

```typescript
import React, { useEffect } from 'react';
import messaging from '@react-native-firebase/messaging';

const App = () => {

  useEffect(() => {
    const unsubscribe = messaging().onMessage(async remoteMessage => {
      // Extract the callback URL from the data payload
      const callbackUrl = remoteMessage.data?.callback;
      if (callbackUrl) {
        try {
          // Send delivery receipt to backend
          await fetch(callbackUrl, {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json',
            },
            body: JSON.stringify({
              status: 'RECEIVED',
            }),
          });
        } catch (error) {
          console.error('[FCM] Error sending callback:', error);
        }
      }
    });

    // Clean up the listener when the component unmounts
    return unsubscribe;
  }, []);

  return (
    // ... Your App Components
  );
};
```

***

**2. Background & Interaction Callbacks**

To track when a user interacts with a notification or receives one in the background, you need to hook into the background and opened-app handlers.

**Notification Clicked (`CLICKED`)**

Triggered when the user taps the notification to open the app.

typescript

```typescript
useEffect(() => {
  // Check if app was opened from a quit state
  messaging().getInitialNotification().then(remoteMessage => {
    if (remoteMessage) {
      handleNotificationCallback(remoteMessage, 'CLICKED');
    }
  });

  // Check if app was opened from background state
  const unsubscribeOpened = messaging().onNotificationOpenedApp(remoteMessage => {
    handleNotificationCallback(remoteMessage, 'CLICKED');
  });

  return unsubscribeOpened;
}, []);

/**
 * Sends a status update to the callback URL provided in the notification payload.
 */
const handleNotificationCallback = async (remoteMessage, status) => {
  const callbackUrl = remoteMessage.data?.callback;

  if (!callbackUrl) return;

  try {
    await fetch(callbackUrl, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ status }),
    });
  } catch (error) {
    console.error(`[FCM] Failed to send ${status} callback:`, error);
  }
};
```

***
