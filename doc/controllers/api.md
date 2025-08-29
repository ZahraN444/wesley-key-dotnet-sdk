# API

```csharp
APIController aPIController = client.APIController;
```

## Class Name

`APIController`

## Methods

* [Createanitem](../../doc/controllers/api.md#createanitem)
* [Getanitemby ID](../../doc/controllers/api.md#getanitemby-id)
* [Create O Auth Token](../../doc/controllers/api.md#create-o-auth-token)
* [Test Endpointwith Arrays](../../doc/controllers/api.md#test-endpointwith-arrays)


# Createanitem

Creates a new resource in the system.

```csharp
CreateanitemAsync(
    Models.Status11Enum status,
    Models.Item body = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`Status11Enum`](../../doc/models/status-11-enum.md) | Template, Required | The status of the items to filter by. |
| `body` | [`Item`](../../doc/models/item.md) | Body, Optional | Custom model with additional properties |

## Response Type

`Task<object>`

## Example Usage

```csharp
Status11Enum status = Status11Enum.Enumvalue3;
Item body = new Item
{
    Id = new Guid("550e8400-e29b-41d4-a716-446655440000"),
    Name = "John Doe",
    Date = DateTime.Parse("2024-05-24"),
    DateTime = DateTime.ParseExact("05/24/2024 12:00:00", "yyyy'-'MM'-'dd'T'HH':'mm':'ss.FFFFFFFK",
        provider: CultureInfo.InvariantCulture,
        DateTimeStyles.RoundtripKind),
    MDecimal = 1234.56,
    MLong = 1234567890123L,
    MBool = true,
    CustomEnum = CustomEnum.VALUE3,
    JsonObject = ApiHelper.JsonDeserialize<object>("{\"key1\":\"val1\",\"key2\":\"val2\"}"),
    Animal = ApiHelper.JsonDeserialize<object>("{\"key1\":\"val1\",\"key2\":\"val2\"}"),
    Map = new Dictionary<string, Message>
    {
        ["key0"] = new Message
        {
            Code = 246,
            Text = "text4",
        },
        ["key1"] = new Message
        {
            Code = 246,
            Text = "text4",
        },
    },
};

try
{
    object result = await aPIController.CreateanitemAsync(
        status,
        body
    );
}
catch (ApiException e)
{
    // TODO: Handle exception here
    Console.WriteLine(e.Message);
}
```

## Example Response

```
{
  "match": "client_mac",
  "name": "cameras",
  "type": "match",
  "values": [
    "010203040506",
    "abcdef*"
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Syntax | `ApiException` |
| 401 | Unauthorized | `ApiException` |
| 403 | Permission Denied | `ApiException` |


# Getanitemby ID

```csharp
GetanitembyIDAsync(
    string id,
    string mValue)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `string` | Template, Required | The ID of the item to retrieve |
| `mValue` | `string` | Query, Required | The value of the item to retrieve |

## Response Type

[`Task<Models.Item>`](../../doc/models/item.md)

## Example Usage

```csharp
string id = "id0";
string mValue = "value2";
try
{
    Item result = await aPIController.GetanitembyIDAsync(
        id,
        mValue
    );
}
catch (ApiException e)
{
    // TODO: Handle exception here
    Console.WriteLine(e.Message);
}
```


# Create O Auth Token

Generates a new OAuth token with the specified scopes.

```csharp
CreateOAuthTokenAsync(
    Models.TokensRequest body = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`TokensRequest`](../../doc/models/tokens-request.md) | Body, Optional | - |

## Response Type

`Task`

## Example Usage

```csharp
try
{
    await aPIController.CreateOAuthTokenAsync();
}
catch (ApiException e)
{
    // TODO: Handle exception here
    Console.WriteLine(e.Message);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | `ApiException` |


# Test Endpointwith Arrays

This endpoint accepts a complex structure with multiple arrays.

```csharp
TestEndpointwithArraysAsync(
    Models.MultipleArraysRequest body = null)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`MultipleArraysRequest`](../../doc/models/multiple-arrays-request.md) | Body, Optional | - |

## Response Type

`Task`

## Example Usage

```csharp
try
{
    await aPIController.TestEndpointwithArraysAsync();
}
catch (ApiException e)
{
    // TODO: Handle exception here
    Console.WriteLine(e.Message);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | `ApiException` |

