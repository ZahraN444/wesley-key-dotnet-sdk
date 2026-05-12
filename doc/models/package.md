
# Package

*This model accepts additional fields of type object.*

## Structure

`Package`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `PackageId` | `string` | Optional | - |
| `Weight` | `double?` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "packageId": "packageId0",
  "weight": 83.8,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

