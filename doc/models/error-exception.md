
# Error Exception

*This model accepts additional fields of type object.*

## Structure

`ErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Error` | `string` | Required | Error code |
| `MessageProperty` | `string` | Required | Human-readable error message |
| `Details` | `object` | Optional | Additional error details |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "error": "invalid_request",
  "message": "The request body is invalid",
  "details": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

