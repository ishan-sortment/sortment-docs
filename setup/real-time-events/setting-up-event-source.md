# Setting up Event Source

## Creating Event Source

Creating an event source is the first step to setting up real-time events in Sortment. You can create a new callback URL and authentication keys against it. Since this is an authenticated URL, it is advised connect the events from server-side, or an event streaming app like Ruddeerstack, Segment etc. Here are the steps to create a new source:

1. In Workspace settings, go to **Event Sources**. Click **Add new source**.
2. Select **Webhook** as a new source type. You can create multiple sources to for different use cases.
3. Following details are required to create a new source:
   1. **Name:** Add name to identify your event source.
   2. **Description:** Add more context to what type of events will be sent via this source. This is an optional parameter
   3. **Event name key path:** This is unique JSON path to the event name key in your payload. For the example below, the event name key path will be `event_metadata.event_name`&#x20;
4. Click **Save**. This will generate a workspace specific _POST URL_.
5. Click **Add key** to generate an _Authorization_ key. This is a private key, do not share it publicly.&#x20;

```json
// Sample event payload
{
  "user_id": "123456789",
  "timestamp": "2024-09-24T14:35:20Z",
  "event_metadata": {
    "event_name": "user_signup",
    "event_properties": {
      "signup_method": "email",
      "referral_code": "REF12345",
      "source": "social_media_ad"
    }
  },
  "user_properties": {
    "user_id": "123456789",
    "first_name": "John",
    "last_name": "Doe",
    "email": "john.doe@email.com",
    "phone_number": "+1234567890",
    "age": 28,
    "gender": "male",
    "location": {
      "city": "New York",
      "country": "USA"
    },
    "subscription_type": "free_trial"
  },
  "device_properties": {
    "device_id": "abcdef123456",
    "device_type": "iPhone",
    "os_version": "iOS 17.0",
    "app_version": "2.3.1",
    "language": "en-US",
    "timezone": "America/New_York"
  }
}
```

## Connect Event Source with Sortment

In the respective app, use the _POST URL_ and _Authorization_ and connect to Sortment. Input your header key name as `Authorization` and value as `Bearer <authorization token>` .

Each request ingests a batch of events into Sortment. We accept up to 2MB uncompressed per request. Events are part of the request body. We support Content-Type application/json.

### Validation

By default, Sortment validates each event and returns a 200 reponse in API response after successfully processing the events. Individually, each event is mapped to its response with validation on whether event was successfully ingested or not. If some events pass validation and others fail, Sortment will ingest the events that pass validation. Some basic requirements for events sent to Sortment are:

* Each event must be properly formatted JSON.
* Each event must contain following keys:
  * Event name at event name key path
  * Timestamp  in ISO-8601 format
  * Distinct ID for event deduplication
* Each event must have fewer than 255 properties.
* All nested object properties must have fewer than 255 keys and max nesting depth is 3.
* Array properties are not supported right now

### Validation Errors

Here's a list of validation errors and how to resolve them:

1. AuthorizationError: Incorrect authorization -> Ensure that your header key name is `Authorization` and value set as `Bearer <authorization token>`
2. MapperError: Event Name Key Missing -> Event name key path set for the source does not exist in the event payload. This is a required field to be sent for each event
3. MapperError: Event not found for Source -> Event being sent is not whitelisted for this source
4. MapperError: Event data type does not match -> Event datatype for a whitelisted key does not match the value received in the payload

