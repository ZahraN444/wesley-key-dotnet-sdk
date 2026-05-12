
# Webhook Registration

*This model accepts additional fields of type object.*

## Structure

`WebhookRegistration`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Url` | `string` | Required | The endpoint URL that will receive webhook events |
| `Events` | [`List<Event>`](../../doc/models/event.md) | Required | List of events to subscribe to |
| `Secret` | `string` | Optional | Secret key for webhook signature verification |
| `Active` | `bool?` | Optional | Whether the webhook is active<br><br>**Default**: `true` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "url": "https://merchant.example.com/webhooks/events",
  "events": [
    "order.created",
    "payment.completed"
  ],
  "secret": "webhook_secret_key_123",
  "active": true,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

