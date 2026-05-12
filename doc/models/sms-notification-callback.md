
# Sms Notification Callback

*This model accepts additional fields of type object.*

## Structure

`SmsNotificationCallback`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `MessageId` | `string` | Optional | - |
| `PhoneNumber` | `string` | Optional | - |
| `Status` | [`Status2?`](../../doc/models/status-2.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "messageId": "sms_002",
  "phoneNumber": "+15551234567",
  "status": "delivered",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

