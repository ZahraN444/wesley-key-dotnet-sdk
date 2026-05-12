
# Inventory Stock Increase Event

*This model accepts additional fields of type object.*

## Structure

`InventoryStockIncreaseEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `InventoryStockIncreaseEventType` | `string` | Required, Constant | **Value**: `"stock.increase"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "inventoryStockIncreaseEventType": "stock.increase",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

