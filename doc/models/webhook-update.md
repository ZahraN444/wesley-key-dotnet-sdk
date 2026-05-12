
# Webhook Update

*This model accepts additional fields of type object.*

## Structure

`WebhookUpdate`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Url` | `string` | Optional | - |
| `Events` | `List<string>` | Optional | - |
| `Secret` | `string` | Optional | - |
| `Active` | `bool?` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "url": "url6",
  "events": [
    "events8",
    "events9"
  ],
  "secret": "secret2",
  "active": false,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

