# SSO login via Okta

Sortment supports Single Sign-On (SSO) using **Okta** as the Identity Provider (IdP). This integration uses **OpenID Connect (OIDC)** for secure authentication and **Just-In-Time (JIT) provisioning** to automatically create users in Sortment when they log in for the first time.

***

### Supported Authentication Flow

* **SP-initiated SSO**: Users start the login flow from Sortment

***

### Requirements

To set up Okta SSO, you must:

* Have access to an Okta tenant
* Be an Okta administrator

***

### Okta Application Configuration

Follow these steps to configure Sortment SSO in Okta:

1. Sign in to the **Okta Admin Console**.
2. Navigate to **Applications > Applications**, then click **Create App Integration**.
3. Select **OIDC – OpenID Connect** as the sign-in method and choose **Web Application**.
4. Enter **Sortment** as the application name.
5. Configure the following settings:
   * **Grant type**: Authorization Code
   *   **Sign-in redirect URIs**:

       ```
       https://app.sortment.com/api/v1/oauth/redirect/okta
       ```
   *   **Sign-out redirect URIs**:

       ```
       https://app.sortment.com/
       ```
   * **Controlled access**: Select who can access this application
6. Click **Save**.

***

### Enable Okta-Initiated Login

For the optimal user experience, we recommend allowing Okta to initiate the login flow.

1. From the application settings page, click **Edit** next to **General Settings**.
2. Set the following options:
   * **Login initiated by**: App and Okta Sign-in Page
   * **Application visibility**: Display application icon to users
   * **Login flow**: Redirect to app to initiate login (OIDC Compliant)
   *   **Initiate login URI**:

       ```
       https://app.sortment.com/api/v1/login/okta
       ```
3. Click **Save** to finish.

***

### Okta Configuration Details

From the Okta application settings page, copy and securely store the following values:

* **Client ID**
* **Client Secret**
* **Okta Domain**&#x20;
* **Issuer URI**

***

#### How to find Okta domain

The Okta domain is the first part of your Okta URL.

**Example**

```
https://dev-123456.okta.com
```

Okta domain:

```
dev-123456.okta.com
```

***

#### How to find Issuer URI

The **Issuer URI** identifies the Okta authorization server used for authentication.

You may use:

*   **Org Authorization Server**

    ```
    https://dev-123456.okta.com
    ```
*   **Default Custom Authorization Server**

    ```
    https://dev-123456.okta.com/oauth2/default
    ```

To find the Issuer URI for a custom authorization server, navigate to **API > Authorization Servers** in the Okta Admin Console and copy the **Issuer URI**.
