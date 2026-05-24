# Whitelist Event Payload

To use any event in Journeys, it needs to be whitelisted on respective source. Here are the steps to whitelist an event payload and its properties on Sortment:

1. Navigate to Sortment Events tab,  represented by the **Mouse Pointer** icon.
2. Click on the **Add Event** button to start setting up a new event. You can either start from scratch or clone an existing event if the event payload structure for this event matches an existing whitelisted event.
3. Choose **Source** from the dropdown and Add sample **Event JSON payload.** This should be a valid JSON to proceed. Click **Next**.
4. Setup the reserved keys by selecting the keys from the payload. Once done, click **Next**.
   1. **User ID**: Unique identifier for the user.
   2. **Distinct ID**: Unique identifier for each event.
   3. **Timestamp**: Time of event action. This should be in ISO-8601 format.
5. Whitelisting event prperties is mandatory to use them in journeys. To whitelist event properties other than reserved keys, click Add Properties button.
6. In the popup, select keys from the event payload and Click **Save**.
7. For each key, pick a Label from existing list or create a new label and set the datatype for this field. This will validate the event key value during event ingestion. Once done, click **Next**.
8. To name the event, two values are necessary:
   1. **Event Name** (as received in the payload): This must match the name as sent in the payload to Sortment (including capitalization, spaces, etc.)
   2. **Event Label**: Concise and readable label for this event. This will be used to identify the event on Sortment in events manager and journeys.
