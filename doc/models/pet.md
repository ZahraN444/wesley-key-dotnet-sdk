
# Pet

## Structure

`Pet`

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
  "id": 120,
  "category": null,
  "name": "name0",
  "photoUrls": [
    "photoUrls5",
    "photoUrls6"
  ],
  "tags": [
    null
  ],
  "status": "available"
}
```

