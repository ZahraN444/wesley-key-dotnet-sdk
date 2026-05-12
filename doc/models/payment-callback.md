
# Payment Callback

*This model accepts additional fields of type object.*

## Structure

`PaymentCallback`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `OrderId` | `string` | Required | - |
| `PaymentStatus` | [`PaymentStatus`](../../doc/models/payment-status.md) | Required | - |
| `TransactionId` | `string` | Required | - |
| `Amount` | `double?` | Optional | - |
| `Currency` | `string` | Optional | - |
| `Timestamp` | `DateTime?` | Optional | - |
| `FailureReason` | `string` | Optional | Reason for payment failure (if applicable) |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "orderId": "order_789",
  "paymentStatus": "success",
  "transactionId": "txn_abc123",
  "amount": 59.98,
  "currency": "USD",
  "timestamp": "09/19/2025 10:35:00",
  "failureReason": "failureReason0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

