
# Inventory Change Event Body

## Class Name

`InventoryChangeEventBody`

## Cases

| Type | Factory Method |
|  --- | --- |
| [`InventoryStockIncreaseEvent`](../../../doc/models/inventory-stock-increase-event.md) | InventoryChangeEventBody.FromInventoryStockIncreaseEvent(InventoryStockIncreaseEvent inventoryStockIncreaseEvent) |
| [`InventoryStockDecreaseEvent`](../../../doc/models/inventory-stock-decrease-event.md) | InventoryChangeEventBody.FromInventoryStockDecreaseEvent(InventoryStockDecreaseEvent inventoryStockDecreaseEvent) |
| [`InventoryStockDepletedEvent`](../../../doc/models/inventory-stock-depleted-event.md) | InventoryChangeEventBody.FromInventoryStockDepletedEvent(InventoryStockDepletedEvent inventoryStockDepletedEvent) |

## InventoryStockIncreaseEvent

### Initialization Code

#### Example

```csharp
InventoryChangeEventBody value = InventoryChangeEventBody.FromInventoryStockIncreaseEvent(
    new InventoryStockIncreaseEvent
    {
        InventoryStockIncreaseEventType = "stock.increase",
    }
);
```

## InventoryStockDecreaseEvent

### Initialization Code

#### Example

```csharp
InventoryChangeEventBody value = InventoryChangeEventBody.FromInventoryStockDecreaseEvent(
    new InventoryStockDecreaseEvent
    {
        InventoryStockDecreaseEventType = "stock.decrease",
    }
);
```

## InventoryStockDepletedEvent

### Initialization Code

#### Example

```csharp
InventoryChangeEventBody value = InventoryChangeEventBody.FromInventoryStockDepletedEvent(
    new InventoryStockDepletedEvent
    {
        InventoryStockDepletedEventType = "stock.depleted",
    }
);
```

