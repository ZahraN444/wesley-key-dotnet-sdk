## Webhooks Handler

Standard webhook group for order and payment events

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name | Description |
|  --- | --- |
| [orderCreated new testing my newy tesingggggg toc hejcjk](../../../doc/events/webhooks/webhooks/order-created-new-testing-my-newy-tesingggggg-toc-hejcjk.md) | Triggered when a new order is created |
| [orderUpdated](../../../doc/events/webhooks/webhooks/order-updated.md) | Triggered when an order is updated |
| [paymentCompleted](../../../doc/events/webhooks/webhooks/payment-completed.md) | Triggered when a payment is successfully processed |
| [primitiveCollectionEvent](../../../doc/events/webhooks/webhooks/primitive-collection-event.md) | Demonstrates oneOf across enum(string), integer, and array types. |

## SDK Usage Example

```csharp
using Microsoft.AspNetCore.Mvc;
using WebhooksAndCallbacksAPI.Standard.Events.Webhooks;
using WebhooksAndCallbacksAPI.Standard.Http.Request;

namespace EventListener.Controller;

[Route("webhooks")]
[ApiController]
public class WebhooksController : ControllerBase
{
    [HttpPost]
    public async Task<IActionResult> ReceiveEvent()
    {
        // Create the HttpRequestData from the incoming HttpRequest
        var eventRequest = HttpRequestData.FromAspNetCoreParams(
            Request.Method,
            Request.Scheme,
            Request.Host.ToString(),
            Request.Path.ToString(),
            Request.QueryString.ToString(),
            Request.Headers,
            Request.Body,
            Request.Query,
            Request.Cookies,
            Request.Protocol,
            Request.ContentType,
            Request.ContentLength
        );

        // Use the provided handler to verify and parse the incoming event
        var handler = new WebhooksHandler("hmac-secret-key");

        var webhooksParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = webhooksParsingResult.MatchSome<string>(
            orderCreatedNewTestingMyNewyTesinggggggTocHejcjk: orderCreatedNewTestingMyNewyTesinggggggTocHejcjk => $"OrderCreatedNewTestingMyNewyTesinggggggTocHejcjk event received {orderCreatedNewTestingMyNewyTesinggggggTocHejcjk}",
            orderUpdated: orderUpdated => $"OrderUpdated event received {orderUpdated}",
            paymentCompleted: paymentCompleted => $"PaymentCompleted event received {paymentCompleted}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

