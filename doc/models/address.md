
# Address

*This model accepts additional fields of type object.*

## Structure

`Address`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Street` | `string` | Required | - |
| `City` | `string` | Required | - |
| `Zip` | `string` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "street": "123 Main St",
  "city": "New York",
  "zip": "10001",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

