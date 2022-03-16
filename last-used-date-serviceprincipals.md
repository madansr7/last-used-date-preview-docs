# Service principal last sign in

The service principal sign in api returns the last signed in date for service principals based on various usage scenarios (delegated auth, app only auth, client vs resource). It provides the ability to review service principal sign in activity.
To consume the API you can start by identifying the application or service principal by calling the /servicePrincipals Microsoft Graph API and then call the application insights API to get last sign in date for the service principal.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

| Permission type                        | Permissions (from least to most privileged) |
| :------------------------------------- | :------------------------------------------ |
| Delegated (work or school account)     | AuditLog.Read.All                           |
| Delegated (personal Microsoft account) | Not supported                               |
| Application                            | AuditLog.Read.All                           |

> [!Note]
> This API will return data only for those service principals for which there was at least one activity logged in time prior to 30 day period. Applications that were created but never used to get a tokens will not show usage.

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET https://graph.microsoft.com/beta/reports/servicePrincipalSignInActivities
```

## Optional query parameters

This method supports the `$top`, `$skiptoken`, and `$filter` OData Query Parameters to help customize the response. For details about how to use these parameters, see [OData query parameters](/graph/query-parameters).

## Request headers

| Name          | Description    |
| :------------ | :------------- |
| Authorization | Bearer {token} |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and collection of `servicePrincipalSignInActivity` objects in the response body.

## Examples

### Example 1: List servicePrincipalSignInActivities

#### Request

The following is an example of the request.

<!-- {
  "blockType": "request",
  "name": "get_serviceprincipal_last_signin_1"
}-->

```http
GET https://graph.microsoft.com/beta/reports/servicePrincipalSignInActivities
```

#### Response

> **Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.signIn"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#reports/servicePrincipalSignInActivities",
  "value": [
    {
      "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3",
      "appId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
      "delegatedClientSignInActivity": {
        "lastSignInDateTime": "2021-01-01T00:00:00-8:00",
        "lastSignInRequestId": "e58c9022-c965-4ec0-960b-9c197e549f27"
      },
      "delegatedResourceSignInActivity": {
        "lastSignInDateTime": "2021-02-01T00:00:00-8:00",
        "lastSignInRequestId": "25570a7f-a031-4f20-959e-02fb7cd46a1c"
      },
      "applicationAuthenticationClientSignInActivity": {
        "lastSignInDateTime": "2021-03-01T00:00:00-8:00",
        "lastSignInRequestId": "4ea8ac36-d43d-431c-bb05-739348e18c66"
      },
      "applicationAuthenticationResourceSignInActivity": {
        "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
        "lastSignInRequestId": "0f251de7-e611-41fb-bed0-6eb650757e72"
      },
      "lastSignInActivity": {
        "lastSignInDateTime": "2021-04-01T00:00:00Z",
        "lastSignInRequestId": "0f251de7-e611-41fb-bed0-6eb650757e72"
      }
    },
    {
      "id": "ZjRkOTY1NGYtMDMwNS00MDcyLTg3OGMtOGJmMjY2ZGZlMTQ2",
      "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
      "delegatedClientSignInActivity": {
        "lastSignInDateTime": "2021-01-01T00:00:00-8:00",
        "lastSignInRequestId": "7e24e4a9-ee1e-45d9-97ff-b4fb0c854b16"
      },
      "delegatedResourceSignInActivity": {
        "lastSignInDateTime": "2021-02-01T00:00:00-8:00",
        "lastSignInRequestId": "3e767241-2173-41f5-a42d-1302549950b2"
      },
      "applicationAuthenticationClientSignInActivity": {
        "lastSignInDateTime": "2021-03-01T00:00:00-8:00",
        "lastSignInRequestId": "0e0cb2c3-85b9-4bdc-8a89-3bd08a5d8548"
      },
      "applicationAuthenticationResourceSignInActivity": {
        "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
        "lastSignInRequestId": "b26f6bf8-af96-4f2a-bef7-07913f634d6d"
      },
      "lastSignInActivity": {
        "lastSignInDateTime": "2021-04-01T00:00:00Z",
        "lastSignInRequestId": "b26f6bf8-af96-4f2a-bef7-07913f634d6d"
      }
    }
  ]
}
```

### Example 2: Get servicePrincipalSignInActivities by entity id

#### Request

The following is an example of the request.

<!-- {
  "blockType": "request",
  "name": "get_serviceprincipal_last_signin_1"
}-->

```http
GET https://graph.microsoft.com/beta/reports/servicePrincipalSignInActivities/ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3
```

#### Response

> **Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.signIn"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
     "@odata.context":"https://graph.microsoft.com/beta/$metadata#reports/servicePrincipalSignInActivities",
     "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3",
     "appId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
     "delegatedClientSignInActivity": {
          "lastSignInDateTime": "2021-01-01T00:00:00-8:00",
          "lastSignInRequestId": "e58c9022-c965-4ec0-960b-9c197e549f27"
     },
     "delegatedResourceSignInActivity": {
          "lastSignInDateTime": "2021-02-01T00:00:00-8:00",
          "lastSignInRequestId": "25570a7f-a031-4f20-959e-02fb7cd46a1c"
     },
     "applicationAuthenticationClientSignInActivity": {
          "lastSignInDateTime": "2021-03-01T00:00:00-8:00",
          "lastSignInRequestId": "4ea8ac36-d43d-431c-bb05-739348e18c66"
     },
     "applicationAuthenticationResourceSignInActivity": {
          "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
          "lastSignInRequestId": "0f251de7-e611-41fb-bed0-6eb650757e72"
     },
     "lastSignInActivity": {
          "lastSignInDateTime": "2021-04-01T00:00:00Z",
          "lastSignInRequestId": "0f251de7-e611-41fb-bed0-6eb650757e72"
     }
}
```

### Example 3: Get servicePrincipalSignInActivities filtered by applicationId

#### Request

<!-- {
  "blockType": "request",
  "name": "get_serviceprincipal_last_signin_3"
}-->

```http
GET https://graph.microsoft.com/beta/reports/servicePrincipalSignInActivities?$filter=appId eq 'f4d9654f-0305-4072-878c-8bf266dfe146'
```

#### Response

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.signIn"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
     "@odata.context":"https://graph.microsoft.com/beta/$metadata#reports/servicePrincipalSignInActivities",
     "id": "ZjRkOTY1NGYtMDMwNS00MDcyLTg3OGMtOGJmMjY2ZGZlMTQ2",
     "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
     "delegatedClientSignInActivity": {
          "lastSignInDateTime": "2021-01-01T00:00:00-8:00",
          "lastSignInRequestId": "7e24e4a9-ee1e-45d9-97ff-b4fb0c854b16"
     },
     "delegatedResourceSignInActivity": {
          "lastSignInDateTime": "2021-02-01T00:00:00-8:00",
          "lastSignInRequestId": "3e767241-2173-41f5-a42d-1302549950b2"
     },
     "applicationAuthenticationClientSignInActivity": {
          "lastSignInDateTime": "2021-03-01T00:00:00-8:00",
          "lastSignInRequestId": "0e0cb2c3-85b9-4bdc-8a89-3bd08a5d8548"
     },
     "applicationAuthenticationResourceSignInActivity": {
          "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
          "lastSignInRequestId": "b26f6bf8-af96-4f2a-bef7-07913f634d6d"
     },
     "lastSignInActivity": {
          "lastSignInDateTime": "2021-04-01T00:00:00Z",
          "lastSignInRequestId": "b26f6bf8-af96-4f2a-bef7-07913f634d6d"
     }
}
```

## Entity types

### servicePrincipalSignInActivity entity

The sign-in activities for a servicePrincipal. Contains information about last usage time of the service principal.

#### Properties

| Property                                          | Type                             | Description                                                                                                                          | Key | ReadOnly |
| ------------------------------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | --- | -------- |
| `id`                                              | `string`                         | The unique id for each service principal sign-in event.                                                                              | Yes | Yes      |
| `appId`                                           | `string`                         | The application id of the resource.                                                                                                  | No  | Yes      |
| `delegatedClientSignInActivity`                   | `microsoft.graph.signInActivity` | The sign-in activity of the application in a delegated flow (user sign in) where the application is acting like a client.            | No  | Yes      |
| `delegatedResourceSignInActivity`                 | `microsoft.graph.signInActivity` | The sign-in activity of the application in a delegated flow (user sign in) where the application is acting like a resource.          | No  | Yes      |
| `applicationAuthenticationClientSignInActivity`   | `microsoft.graph.signInActivity` | The sign-in activity of the application in a app-only auth flow (app to app tokens) where the application is acting like a client.   | No  | Yes      |
| `applicationAuthenticationResourceSignInActivity` | `microsoft.graph.signInActivity` | The sign-in activity of the application in a app-only auth flow (app to app tokens) where the application is acting like a resource. | No  | Yes      |

#### Supported functionality

| Operation | Supported | Method        | Success |
| --------- | :-------: | ------------- | ------- |
| List      |     ✓     | `GET`         | `200`   |
| Get       |     ✓     | `GET`         | `200`   |
| Create    |     X     | `POST`        | `201`   |
| Update    |     X     | `PATCH`/`PUT` | `204`   |
| Delete    |     X     | `DELETE`      | `204`   |

#### Supported query patterns

| Pattern                | Supported | Syntax                                                                                                               |
| ---------------------- | :-------: | -------------------------------------------------------------------------------------------------------------------- |
| Server-side pagination |     ✓     | `@odata.nextLink`                                                                                                    |
| Filter                 |     ✓     | `/servicePrincipalSignInActivities?$filter=delegatedClientSignInActivity/lastSignInDateTime lt 2020-01-01T00:00:00Z` |
| Filter                 |     ✓     | `/servicePrincipalSignInActivities?$filter=appId eq 'f4d9654f-0305-4072-878c-8bf266dfe146'`                          |

### reportRoot entity (existing)

#### New properties

| Property                           | Type                                              | Description                                                                                                         | Key | ReadOnly |
| ---------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --- | -------- |
| `servicePrincipalSignInActivities` | `Collection(self.servicePrincipalSignInActivity)` | The sign in activities for a servicePrincipal. Contains information about last usage time of the service principal. | No  | Yes      |

#### CSDL

```xml

<EntityType Name="reportRoot" OpenType="false">
    <NavigationProperty Name="servicePrincipalSignInActivities" Type="Collection(self.servicePrincipalSignInActivity)" ContainsTarget="true" />
</EntityType>

```
