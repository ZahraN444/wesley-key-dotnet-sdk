## Callbacks B Handler

Notification delivery callback group with discriminator mapping

Events in this group are uniquely identified by the `notificationType` field.

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name | Description | Event Identifier |
|  --- | --- | --- |
| [emailNotificationCallback](../../../doc/events/callbacks/callbacks_b/email-notification-callback.md) | Called when email notification delivery is complete | email |
| [smsNotificationCallback](../../../doc/events/callbacks/callbacks_b/sms-notification-callback.md) | Called when SMS notification delivery is complete | sms |

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
            smsNotificationCallback: smsNotificationCallback => $"SmsNotificationCallback event received {smsNotificationCallback}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

