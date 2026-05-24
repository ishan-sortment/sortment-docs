# Meta (Facebook)

## Overview

Sortment lets you send broadcast messages via your existing Meta WhatsApp Business account. It is required to have access to your Meta Business Account before configuring the same on Sortment.&#x20;

## Set up your Meta account on Sortment

1. Navigate to channels&#x20;
2. Under, WhatsApp channel, select Meta as the provider
3. Add the following details&#x20;
   1. Name: Provide a name that would help you identify the configured account.&#x20;
   2. **Phone Number ID:** This can be found in Meta's App Dashboard
   3. **WhatsApp Business Account ID:** You will get it from Business Settings -> Accounts -> WhatsApp Accounts -> Account Name. On top right corner, you will find WABA ID
   4. **Access Token:** This allows Sortment to fetch the templates verified by Meta directly.

{% hint style="warning" %}
Follow the steps here to get **Phone Number ID** for your from your Meta dashboard: [#step-3-get-phone-number-id](add-new-phone-number-to-meta.md#step-3-get-phone-number-id "mention")
{% endhint %}



#### How To Get System User Access Token

1. Log onto [business.facebook.com](https://business.facebook.com).
2. Open **Settings > System users**.
3. Add a system user with **Admin** role
4. Under **assigned assets**:
   * Give the permission of the app that has been created.
   * All permissions c.an be given.
5. Click on **Generate token**.
   * Select the relevant app.
   * Under **token expiration**, choose **Never**.
   * Under **permissions**, add the following permissions:
     * `WhatsApp_business_management`
     * `WhatsApp_business_messaging`

#### How To Add Callback URL

1. Log onto [developers.facebook.com](https://developers.facebook.com).
2. Go to the **My Apps** section and choose the relevant app.
3. Go to **Webhooks**.
4. Under **Messages**, select:
   * `message_template_quality_update`
   * `message_template_status_update`
   * Choose **Version V18**.
5. Click on **Subscribe**.
6. Then click on **Edit Subscription**.
   * Ensure the dropdown reads **WhatsApp business token**.
   * Add the following callback URL: https://callback.fyno.io/?fyno-provider=meta
