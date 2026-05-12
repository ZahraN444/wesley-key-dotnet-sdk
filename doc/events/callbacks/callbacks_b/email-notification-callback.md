
# Email Notification Callback

Called when email notification delivery is complete

## Signature Verification

This event uses the `HMAC Signature Verifier` for request verification. The event includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Headers

This event's request contains the following headers.

| Name |
|  --- |
| Content-Type |

## Payload Type

This event's request payload is of type [NotificationCallback](../../../../doc/models/notification-callback.md).

## Payload Example

```json
{
  "notificationType": "email",
  "subject": "Order Coonfirmation",
  "message": "msg_email_789",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

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
        var handler = new CallbacksBHandler("hmac-secret-key");

        var callbacksBParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = callbacksBParsingResult.MatchSome<string>(
            emailNotificationCallback: emailNotificationCallback => $"EmailNotificationCallback event received {emailNotificationCallback}",
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
| 200 | Callback received successfully |
| 422 | Callback processing failed |

