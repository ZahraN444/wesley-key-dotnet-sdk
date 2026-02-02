
# Getting Started with Cypress Test API

## Introduction

This is a sample API to demonstrate an OpenAPI spec with multiple endpoints and a custom model.

## Install the Package

If you are building with .NET CLI tools then you can also use the following command:

```bash
dotnet add package WesleyKeySDK --version 3.0.3
```

You can also view the package at:
https://www.nuget.org/packages/WesleyKeySDK/3.0.3

## Test the SDK

The generated SDK also contain one or more Tests, which are contained in the Tests project. In order to invoke these test cases, you will need `NUnit 3.0 Test Adapter Extension` for Visual Studio. Once the SDK is complied, the test cases should appear in the Test Explorer window. Here, you can click `Run All` to execute these test cases.

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| DefaultHost | `string` | *Default*: `"www.example.com"` |
| Environment | `Environment` | The API environment. <br> **Default: `Environment.Production`** |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(100)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |

The API client can be initialized as follows:

### Code-Based Initialization

```csharp
using CypressTestAPI.Standard;

namespace ConsoleApp;

CypressTestAPIClient client = new CypressTestAPIClient.Builder()
    .Environment(CypressTestAPI.Standard.Environment.Production)
    .DefaultHost("www.example.com")
    .Build();
```

### Configuration-Based Initialization

```csharp
using CypressTestAPI.Standard;
using Microsoft.Extensions.Configuration;

namespace ConsoleApp;

// Build the IConfiguration using .NET conventions (JSON, environment, etc.)
var configuration = new ConfigurationBuilder()
    .AddJsonFile("config.json")
    .AddEnvironmentVariables() // [optional] read environment variables
    .Build();

// Instantiate your SDK and configure it from IConfiguration
var client = CypressTestAPIClient
    .FromConfiguration(configuration.GetSection("CypressTestAPI"));
```

See the [Configuration-Based Initialization](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/configuration-based-initialization.md) section for details.

## List of APIs

* [API](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/controllers/api.md)

## SDK Infrastructure

### Configuration

* [Configuration-Based Initialization](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/configuration-based-initialization.md)
* [HttpClientConfiguration](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-client-configuration.md)
* [HttpClientConfigurationBuilder](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-client-configuration-builder.md)
* [ProxyConfigurationBuilder](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/proxy-configuration-builder.md)

### HTTP

* [HttpCallback](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-callback.md)
* [HttpContext](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-context.md)
* [HttpRequest](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-request.md)
* [HttpResponse](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-response.md)
* [HttpStringResponse](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/http-string-response.md)

### Utilities

* [ApiException](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/api-exception.md)
* [ApiHelper](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/api-helper.md)
* [CustomDateTimeConverter](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/custom-date-time-converter.md)
* [UnixDateTimeConverter](https://www.github.com/ZahraN444/wesley-key-dotnet-sdk/tree/3.0.3/doc/unix-date-time-converter.md)

