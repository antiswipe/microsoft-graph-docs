# Create identityProvider

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Create a new [identityProvider](../resources/identityProvider.md) by specifying display name, identityProvider type, client ID, and client secret.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](../../../concepts/permissions_reference.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account)|IdentityProvider.ReadWrite.All|
|Delegated (personal Microsoft account)| Not supported.|
|Application|Not supported.|

The work or school account must be a global administrator of the tenant.

## HTTP request

```http
POST /identityProviders
Content-type: application/json
{
    "name": "string",
    "type": "string",
    "clientId": "string",
    "clientSecret": "string"
}
```

## Request headers

|Name|Description|
|:---------------|:----------|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body

In the request body, provide a JSON representation of [identityProvider](../resources/identityProvider.md) object. All the properties listed in the following table are required.

|Property|Type|Description|
|:---------------|:--------|:----------|
|clientId|String|The client ID for the application. This is the client ID obtained when registering the application with the identity provider.|
|clientSecret|String|The client secret for the application. This is the client secret obtained when registering the application with the identity provider.|
|name|String|The display name of the identity provider.|
|type|String|The identity provider type. It must be one of the following values: <li/>Microsoft<li/>Google<li/>Amazon<li/>LinkedIn<li/>Facebook|

## Response

If successful, this method returns `201, Created` response code and [identityProvider](../resources/identityProvider.md) object in the response body. If unsuccessful, a `4xx` error will be returned with specific details.

## Example

The following example creates an **identityProvider**.

##### Request

```http
POST https://graph.microsoft.com/beta/identityProviders
Content-type: application/json
{
    "name": "Login with Amazon",
    "type": "Amazon",
    "clientId": "56433757-cadd-4135-8431-2c9e3fd68ae8",
    "clientSecret": "000000000000"
}
```

##### Response

```http
HTTP/1.1 201 Created
Content-type: application/json
{
    "id": "Amazon-OAUTH",
    "name": "Login with Amazon",
    "type": "Amazon",
    "clientId": "56433757-cadd-4135-8431-2c9e3fd68ae8",
    "clientSecret": "*****"
}
```