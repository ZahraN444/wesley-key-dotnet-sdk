## Webhooks C Handler

Primitive and collection variant webhook group.

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Webhook-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name |
|  --- |
| [stringEvent](../../../doc/events/webhooks/webhooks_c/string-event.md) |
| [intEvent](../../../doc/events/webhooks/webhooks_c/int-event.md) |
| [numberListEvent](../../../doc/events/webhooks/webhooks_c/number-list-event.md) |
| [stringMapEvent](../../../doc/events/webhooks/webhooks_c/string-map-event.md) |

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
        var handler = new WebhooksCHandler("hmac-secret-key");

        var webhooksCParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = webhooksCParsingResult.MatchSome<string>(
            stringEvent: stringEvent => $"StringEvent event received {stringEvent}",
            intEvent: intEvent => $"IntEvent event received {intEvent}",
            numberListEvent: numberListEvent => $"NumberListEvent event received {numberListEvent}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

