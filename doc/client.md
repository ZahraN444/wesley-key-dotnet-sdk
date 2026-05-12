
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(50)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](../doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](../doc/log-builder.md) | Represents the logging configuration builder for API calls |
| ApiKeyCredentials | [`ApiKeyCredentials`](auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| BearerAuthCredentials | [`BearerAuthCredentials`](auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |

The API client can be initialized as follows:

## Code-Based Initialization

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

## Configuration-Based Initialization

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

See the [Configuration-Based Initialization](../doc/configuration-based-initialization.md) section for details.

## Webhooks and Callbacks APIClient Class

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

### Controllers

| Name | Description |
|  --- | --- |
| OrdersApi | Gets OrdersApi. |

### Properties

| Name | Description | Type |
|  --- | --- | --- |
| HttpClientConfiguration | Gets the configuration of the Http Client associated with this client. | [`IHttpClientConfiguration`](../doc/http-client-configuration.md) |
| Timeout | Http client timeout. | `TimeSpan` |
| Environment | Current API environment. | `Environment` |
| ApiKeyCredentials | Gets the credentials to use with ApiKey. | [`IApiKeyCredentials`](auth/custom-header-signature.md) |
| BearerAuthCredentials | Gets the credentials to use with BearerAuth. | [`IBearerAuthCredentials`](auth/oauth-2-bearer-token.md) |

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `GetBaseUri(Server alias = Server.Default)` | Gets the URL for a particular alias in the current environment and appends it with template parameters. | `string` |
| `ToBuilder()` | Creates an object of the Webhooks and Callbacks APIClient using the values provided for the builder. | `Builder` |

## Webhooks and Callbacks APIClient Builder Class

Class to build instances of Webhooks and Callbacks APIClient.

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `HttpClientConfiguration(Action<`[`HttpClientConfiguration.Builder`](../doc/http-client-configuration-builder.md)`> action)` | Gets the configuration of the Http Client associated with this client. | `Builder` |
| `Timeout(TimeSpan timeout)` | Http client timeout. | `Builder` |
| `Environment(Environment environment)` | Current API environment. | `Builder` |
| `ApiKeyCredentials(Action<ApiKeyModel.Builder> action)` | Sets credentials for ApiKey. | `Builder` |
| `BearerAuthCredentials(Action<BearerAuthModel.Builder> action)` | Sets credentials for BearerAuth. | `Builder` |

