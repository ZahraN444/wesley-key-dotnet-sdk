# Orders

Order management operations

```csharp
OrdersApi ordersApi = client.OrdersApi;
```

## Class Name

`OrdersApi`


# Create Order

Creates a new order and triggers callbacks for payment processing

```csharp
CreateOrderAsync(
    Models.CreateOrderRequest body)
```

## Authentication

This endpoint requires [ApiKey](../../doc/auth/custom-header-signature.md) **OR** [BearerAuth](../../doc/auth/oauth-2-bearer-token.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`CreateOrderRequest`](../../doc/models/create-order-request.md) | Body, Required | - |

## Response Type

**201**: Order created successfully

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.Order](../../doc/models/order.md).

## Related Callbacks

| Name | Description |
|  --- | --- |
| [Payment Callback](../../doc/events/callbacks/callbacks_a/payment-callback.md) | Called when payment processing is complete |
| [Fulfillment Callback](../../doc/events/callbacks/callbacks_a/fulfillment-callback.md) | Called when order processing is complete |
| [Email Notification Callback](../../doc/events/callbacks/callbacks_b/email-notification-callback.md) | Called when email notification delivery is complete |
| [Sms Notification Callback](../../doc/events/callbacks/callbacks_b/sms-notification-callback.md) | Called when SMS notification delivery is complete |

## Example Usage

```csharp
CreateOrderRequest body = new CreateOrderRequest
{
    CustomerId = "cust_12345",
    Items = new List<OrderItem>
    {
        new OrderItem
        {
            ProductId = "prod_001",
            Quantity = 2,
            Price = 29.99,
        },
    },
    CallbackUrl = "https://merchant.example.com/callbacks/payment",
};

try
{
    ApiResponse<Order> result = await ordersApi.CreateOrderAsync(body);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
    if (e is ErrorException)
    {
       // TODO: Handle ErrorException exception here
    }
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid request | [`ErrorException`](../../doc/models/error-exception.md) |

