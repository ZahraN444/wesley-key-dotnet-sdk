
# Inventory Stock Decrease Event

*This model accepts additional fields of type object.*

## Structure

`InventoryStockDecreaseEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `InventoryStockDecreaseEventType` | `string` | Required, Constant | **Value**: `"stock.decrease"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "inventoryStockDecreaseEventType": "stock.decrease",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

