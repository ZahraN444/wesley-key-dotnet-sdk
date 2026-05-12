
# Webhook

*This model accepts additional fields of type object.*

## Structure

`Webhook`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `WebhookId` | `string` | Optional | - |
| `CreatedAt` | `DateTime?` | Optional | - |
| `UpdatedAt` | `DateTime?` | Optional | - |
| `LastDelivery` | `DateTime?` | Optional | Timestamp of the last successful delivery |
| `DeliveryCount` | `int?` | Optional | Total number of events delivered |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "webhookId": "webhook_456",
  "createdAt": "09/19/2025 09:00:00",
  "updatedAt": "09/19/2025 09:00:00",
  "deliveryCount": 42,
  "lastDelivery": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

