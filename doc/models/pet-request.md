
# Pet Request

## Structure

`PetRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Id` | `long?` | Optional | - |
| `Category` | [`Category2`](../../doc/models/category-2.md) | Optional | - |
| `Name` | `string` | Required | - |
| `PhotoUrls` | `List<string>` | Required | - |
| `Tags` | [`List<Tag>`](../../doc/models/tag.md) | Optional | - |
| `Status` | [`StatusEnum?`](../../doc/models/status-enum.md) | Optional | - |

## Example (as JSON)

```json
{
  "id": 198,
  "category": null,
  "name": "name4",
  "photoUrls": [
    "photoUrls9"
  ],
  "tags": [
    null,
    {},
    {}
  ],
  "status": "pending"
}
```

