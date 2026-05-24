# Gupshup Enterprise

## Overview

Sortment lets you send broadcast messages via your existing Gupshup enterprise account. It is required to set up / have a Gupshup account before configuring the same on Sortment.&#x20;

## Set up your Gupshup account on Sortment

1. Navigate to channels&#x20;
2. Under, WhatsApp channel, select Gupshup as the provider
3. Add the following details&#x20;
   1. Name: Provide a name that would help you identify the configured account.&#x20;
   2. Username: Provide the username that you use to sign into your Gupshup Enterprise Account.
   3. Password: Provide the password that you use to sign in, corresponding to the same Gupshup Enterprise account&#x20;

## Set up Callback for events

This will allow Sortment to listen to necessary events to augment analytics and further audience creation.&#x20;

To set up the same,&#x20;

1. Log in to your Gupshup Analytics account.&#x20;
2. On the left navigation pane, click on **Integrations**.&#x20;
3. On Integrations page, find **Webhooks** in navigation pane and click on **WhatsApp Message Delivery Events**.&#x20;
4. Add the follwoing URL as **Notification Callback URL** and select the forward method as **JSONBODY** and click on Submit.
   1. The URL to be used here is: [https://callback.fyno.io/?fyno-provider=gupshup](https://callback.fyno.io/?fyno-provider=gupshup)



<br>
