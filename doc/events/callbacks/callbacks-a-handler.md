## Callbacks A Handler

Payment and fulfillment callback group with custom verification

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name | Description |
|  --- | --- |
| [paymentCallback](../../../doc/events/callbacks/callbacks_a/payment-callback.md) | Called when payment processing is complete |
| [fulfillmentCallback](../../../doc/events/callbacks/callbacks_a/fulfillment-callback.md) | Called when order processing is complete |

## SDK Usage Example

```csharp
using Microsoft.AspNetCore.Mvc;
using WebhooksAndCallbacksAPI.Standard.Events.Callbacks;
using WebhooksAndCallbacksAPI.Standard.Http.Request;

namespace EventListener.Controller;

[Route("callbacks")]
[ApiController]
public class CallbacksController : ControllerBase
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
        var handler = new CallbacksAHandler("hmac-secret-key");

        var callbacksAParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = callbacksAParsingResult.MatchSome<string>(
            paymentCallback: paymentCallback => $"PaymentCallback event received {paymentCallback}",
            fulfillmentCallback: fulfillmentCallback => $"FulfillmentCallback event received {fulfillmentCallback}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

