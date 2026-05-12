
# Order Created Event Delivery Details

## Class Name

`OrderCreatedEventDeliveryDetails`

## Cases

| Type | Factory Method |
|  --- | --- |
| `string` | OrderCreatedEventDeliveryDetails.FromString(string mString) |
| [`DeliveryDetails`](../../../doc/models/delivery-details.md) | OrderCreatedEventDeliveryDetails.FromDeliveryDetails(DeliveryDetails deliveryDetails) |

## string

### Initialization Code

#### Example

```csharp
OrderCreatedEventDeliveryDetails value = OrderCreatedEventDeliveryDetails.FromString("String0");
```

## DeliveryDetails

### Initialization Code

#### Example

```csharp
OrderCreatedEventDeliveryDetails value = OrderCreatedEventDeliveryDetails.FromDeliveryDetails(
    new DeliveryDetails
    {
    }
);
```

