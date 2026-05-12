## Webhooks A Handler

Advanced webhook group for payment status events

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name | Description |
|  --- | --- |
| [paymentStatusUpdated](../../../doc/events/webhooks/webhooks_a/payment-status-updated.md) | Triggered when a payment status is updated via POST method |
| [paymentStatusCreated](../../../doc/events/webhooks/webhooks_a/payment-status-created.md) | Triggered when a new payment status is created |

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
        var handler = new WebhooksAHandler("hmac-secret-key");

        var webhooksAParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = webhooksAParsingResult.MatchSome<string>(
            paymentStatusUpdated: paymentStatusUpdated => $"PaymentStatusUpdated event received {paymentStatusUpdated}",
            paymentStatusCreated: paymentStatusCreated => $"PaymentStatusCreated event received {paymentStatusCreated}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

