
# Order Updated

Triggered when an order is updated

## Signature Verification

This event uses the `HMAC Signature Verifier` for request verification. The event includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Headers

This event's request contains the following headers.

| Name |
|  --- |
| Content-Type |

## Payload Type

This event's request payload is of type [OrderUpdatedEvent](../../../../doc/models/order-updated-event.md).

## Payload Example

```json
{
  "orderUpdatedId": 91,
  "eventType": "order.updated",
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
        var handler = new WebhooksHandler("hmac-secret-key");

        var webhooksParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = webhooksParsingResult.MatchSome<string>(
            orderUpdated: orderUpdated => $"OrderUpdated event received {orderUpdated}",
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

