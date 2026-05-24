# APNs (Apple Push Notification services)

### Prerequisites for Integration with Sortment

Before proceeding, please make sure you have the following:

* A Mac computer with the latest version of Xcode installed
* An Apple Developer account (Individual or Organisation)
* A registered iOS device for testing

***

### Setting up an Apple Developer Account

1. Go to the [Apple Developer website](https://developer.apple.com).
2. Click **"Account"** in the top right corner.
3. Sign in with your Apple ID, or create a new one if necessary.
4. Enrol in the Apple Developer Program by following the on-screen instructions. Note that there is an annual membership fee.
5. Once enrolled, sign in to your Apple Developer account.

***

### Generating a Private Key, Team ID, and Key ID

1. Sign in to your Apple Developer account.
2. In the left-hand menu, select **"Certificates, Identifiers & Profiles."**
3. Under **"Keys,"** click the **"+"** button to create a new key.
4. Enter a descriptive name for the key, enable **"Apple Push Notifications service (APNs),"** and click **"Continue."**
5.  Review the details, click **"Register,"** and then click **"Download"** to save the private key (`.p8` file) to your computer.

    > **Important:** This is the only time you can download this key — store it in a safe place.
6. Note your **Team ID** and **Key ID** from the respective columns in the "Keys" section.

***

### Configuring Application with Sortment

1. Sign up for a Sortment account or sign in if you already have one.
2. Navigate to **Workspace Settings → Sender Profiles**. Under the "Add integration" section, click on the **APNs** button
3. Give a custom integration name of your choice.
4. Select between **Production / Development** environment as per your current application state.
5. Copy/paste the downloaded private key (`.p8` file) from the previous section.
6. Enter your **Team ID** and **Key ID** in their respective fields.
7. Enter your **App Bundle ID**, which you can find in Xcode:
   * Open your project in Xcode.
   * Select the top project item in the Project Navigator on the left.
   * Go to **TARGETS → General**.
   * The **Bundle Identifier** is found under **Identity**.
8. Click **"Save"** to complete the configuration.
