
# Custom Header Signature



Documentation for accessing and setting credentials for ApiKey.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| XAPIKey | `string` | API key for authentication | `XAPIKey` | `XAPIKey` |



**Note:** Auth credentials can be set using `ApiKeyCredentials` in the client builder and accessed through `ApiKeyCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```csharp
using WebhooksAndCallbacksAPI.Standard;
using WebhooksAndCallbacksAPI.Standard.Authentication;

namespace ConsoleApp;

WebhooksAndCallbacksAPIClient client = new WebhooksAndCallbacksAPIClient.Builder()
    .ApiKeyCredentials(
        new ApiKeyModel.Builder(
            "X-API-Key"
        )
        .Build())
    .Build();
```


