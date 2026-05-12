
# Payment Status Updated

Triggered when a payment status is updated via POST method

## Signature Verification

This event uses the `HMAC Signature Verifier` for request verification. The event includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Headers

This event's request contains the following headers.

| Name |
|  --- |
| Content-Type |

## Payload Type

This event's request payload is of type [PaymentStatusUpdatedEvent](../../../../doc/models/payment-status-updated-event.md).

## Payload Example

```json
{
  "paymentStatusId": "ps_123",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

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
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

## Accepted Server Responses

The server should responds with one of the following status codes:

| Status Code | Description |
|  --- | --- |
| 200 | Event processed successfully |
| 422 | Event processing failed |

