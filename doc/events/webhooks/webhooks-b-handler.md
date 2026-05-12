## Webhooks B Handler

Multi-event webhook group with oneOf payload structures. Uses a message template that also includes a request header pointer.

## Signature Verification

This handler uses the `HMAC Signature Verifier` for request verification. Each event in this group includes an `X-Webhook-Signature` header that will be validated using your shared `secret-key` to ensure request authenticity.

## Events

Events available in this group. Subscribe to receive webhook notifications when these events occur.

| Name | Description |
|  --- | --- |
| [userNotificationEvent](../../../doc/events/webhooks/webhooks_b/user-notification-event.md) | Triggered when user-related notifications occur |
| [systemNotificationEvent](../../../doc/events/webhooks/webhooks_b/system-notification-event.md) | Triggered when system-wide notifications occur |
| [inventoryChangeEvent](../../../doc/events/webhooks/webhooks_b/inventory-change-event.md) | Triggered when inventory stock levels change |

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
        var handler = new WebhooksBHandler("hmac-secret-key");

        var webhooksBParsingResult = await handler.VerifyAndParseEventAsync(eventRequest);
        var result = webhooksBParsingResult.MatchSome<string>(
            userNotificationEvent: userNotificationEvent => $"UserNotificationEvent event received {userNotificationEvent}",
            systemNotificationEvent: systemNotificationEvent => $"SystemNotificationEvent event received {systemNotificationEvent}",
            inventoryChangeEvent: inventoryChangeEvent => $"InventoryChangeEvent event received {inventoryChangeEvent}",
            signatureVerificationFailed: error => $"Signature verification failed {error}",
            unknown: () => "Unknown event received"
        );

        return Ok();
    }
}
```

