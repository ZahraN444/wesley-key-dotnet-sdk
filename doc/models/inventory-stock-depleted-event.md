
# Inventory Stock Depleted Event

*This model accepts additional fields of type object.*

## Structure

`InventoryStockDepletedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `InventoryStockDepletedEventType` | `string` | Required, Constant | **Value**: `"stock.depleted"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "inventoryStockDepletedEventType": "stock.depleted",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

