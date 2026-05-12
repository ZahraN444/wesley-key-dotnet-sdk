
# Getting Started with Webhooks and Callbacks API

## Introduction

A comprehensive API demonstrating webhooks and callbacks patterns.

### Webhooks

Webhooks allow your application to receive real-time notifications when certain events occur.

### Callbacks

Callbacks are used for asynchronous operations where the API will call back to your provided URL when the operation completes.

## Install the Package

If you are building with .NET CLI tools then you can also use the following command:

```bash
dotnet add package WesleyKeySDK --version 4.0.0
```

You can also view the package at:
https://www.nuget.org/packages/WesleyKeySDK/4.0.0

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(50)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](doc/log-builder.md) | Represents the logging configuration builder for API calls |
| ApiKeyCredentials | [`ApiKeyCredentials`](doc/auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| BearerAuthCredentials | [`BearerAuthCredentials`](doc/auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |

The API client can be initialized as follows:

### Code-Based Initialization

```csharp
using Microsoft.Extensions.Logging;
using WebhooksAndCallbacksAPI.Standard;
using WebhooksAndCallbacksAPI.Standard.Authentication;

namespace ConsoleApp;

WebhooksAndCallbacksAPIClient client = new WebhooksAndCallbacksAPIClient.Builder()
    .ApiKeyCredentials(
        new ApiKeyModel.Builder(
            "X-API-Key"
        )
        .Build())
    .BearerAuthCredentials(
        new BearerAuthModel.Builder(
            "AccessToken"
        )
        .Build())
    .HttpClientConfig(httpClientConfig =>
        httpClientConfig.Timeout(TimeSpan.FromSeconds(100)))
    .LoggingConfig(config => config
        .LogLevel(LogLevel.Information)
        .RequestConfig(reqConfig => reqConfig.Body(true))
        .ResponseConfig(respConfig => respConfig.Headers(true))
    )
    .Build();
```

### Configuration-Based Initialization

```csharp
using WebhooksAndCallbacksAPI.Standard;
using Microsoft.Extensions.Configuration;

namespace ConsoleApp;

// Build the IConfiguration using .NET conventions (JSON, environment, etc.)
var configuration = new ConfigurationBuilder()
    .AddJsonFile("config.json")
    .AddEnvironmentVariables() // [optional] read environment variables
    .Build();

// Instantiate your SDK and configure it from IConfiguration
var client = WebhooksAndCallbacksAPIClient
    .FromConfiguration(configuration.GetSection("WebhooksAndCallbacksAPI"));
```

See the [Configuration-Based Initialization](doc/configuration-based-initialization.md) section for details.

## Authorization

This API uses the following authentication schemes.

* [`ApiKey (Custom Header Signature)`](doc/auth/custom-header-signature.md)
* [`BearerAuth (OAuth 2 Bearer token)`](doc/auth/oauth-2-bearer-token.md)

## List of APIs

* [Orders](doc/controllers/orders.md)

## Webhooks

* [Webhooks](doc/events/webhooks/webhooks-handler.md)
* [Webhooks A](doc/events/webhooks/webhooks-a-handler.md)
* [Webhooks B](doc/events/webhooks/webhooks-b-handler.md)
* [Webhooks C](doc/events/webhooks/webhooks-c-handler.md)
* [Webhooks No Verification](doc/events/webhooks/webhooks-no-verification-handler.md)

## SDK Infrastructure

### Configuration

* [Configuration-Based Initialization](doc/configuration-based-initialization.md)
* [HttpClientConfiguration](doc/http-client-configuration.md)
* [HttpClientConfigurationBuilder](doc/http-client-configuration-builder.md)
* [LogBuilder](doc/log-builder.md)
* [LogRequestBuilder](doc/log-request-builder.md)
* [LogResponseBuilder](doc/log-response-builder.md)
* [ProxyConfigurationBuilder](doc/proxy-configuration-builder.md)

### HTTP

* [HttpCallback](doc/http-callback.md)
* [HttpContext](doc/http-context.md)
* [HttpRequest](doc/http-request.md)
* [HttpRequestData](doc/http-request-data.md)
* [HttpResponse](doc/http-response.md)
* [HttpStringResponse](doc/http-string-response.md)

### Utilities

* [ApiException](doc/api-exception.md)
* [ApiResponse](doc/api-response.md)
* [ApiHelper](doc/api-helper.md)
* [CustomDateTimeConverter](doc/custom-date-time-converter.md)
* [UnixDateTimeConverter](doc/unix-date-time-converter.md)

