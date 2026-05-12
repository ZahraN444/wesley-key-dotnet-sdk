
# Order Created Event

*This model accepts additional fields of type object.*

## Structure

`OrderCreatedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `OrderId` | `string` | Required | - |
| `FulfillmentStatus` | [`FulfillmentStatus`](../../doc/models/fulfillment-status.md) | Required | - |
| `TrackingNumber` | `string` | Optional | - |
| `Carrier` | `string` | Optional | - |
| `Scopes` | [`List<OauthScopeOauthACG>`](../../doc/models/oauth-scope-oauth-acg.md) | Optional | List of scopes that apply to the OAuth token<br><br>**Constraints**: *Unique Items Required* |
| `EstimatedDelivery` | `DateTime?` | Optional | - |
| `Timestamp` | `DateTime?` | Optional | - |
| `Document` | `Stream` | Optional | Binary file upload |
| `TotalWeight` | `double?` | Optional | - |
| `Price` | `double?` | Optional | - |
| `Quantity` | `int?` | Optional | - |
| `LongId` | `long?` | Optional | - |
| `Fragile` | `bool?` | Optional | - |
| `Notes` | `string` | Optional | Explicitly nullable field |
| `Items` | `List<string>` | Optional | - |
| `Packages` | [`List<Package>`](../../doc/models/package.md) | Optional | - |
| `Address` | [`Address`](../../doc/models/address.md) | Optional | - |
| `Metadata` | `object` | Optional | - |
| `Attributes` | `Dictionary<string, string>` | Optional | - |
| `DeliveryDetails` | [`OrderCreatedEventDeliveryDetails`](../../doc/models/containers/order-created-event-delivery-details.md) | Optional | This is a container for one-of cases. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "orderId": null,
  "fulfillmentStatus": "fulfilled",
  "carrier": "FedEx",
  "estimatedDelivery": "2025-09-22",
  "timestamp": "09/19/2025 14:00:00",
  "totalWeight": 12.75,
  "price": 199.99,
  "quantity": 5,
  "longId": 9223372036854775807,
  "fragile": true,
  "items": [
    "item1",
    "item2"
  ],
  "packages": [
    {
      "packageId": "PKG123",
      "weight": 2.5
    }
  ],
  "address": {
    "street": "123 Main St",
    "city": "New York",
    "zip": "10001"
  },
  "metadata": {
    "customField1": "value",
    "customField2": 123
  },
  "attributes": {
    "color": "red",
    "size": "XL"
  },
  "deliveryDetails": {
    "method": "express",
    "eta": "2025-09-21T12:00:00Z"
  },
  "trackingNumber": "trackingNumber2",
  "scopes": [
    "file_requests.read"
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

