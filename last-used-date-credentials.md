# Application credential last used API

Get data and insights when an application credential was used last. This API provides an admin with the ability to investigate application or service principal credential usage.
A user would first identify the application or service principal by calling the /applications or /servicePrincipals API and then call the credential insights API to get last used date for every credential in that application.
Alternatively they could get the last used date for an application or service principal from the signInActivity API and then query the credential insights API to get the last used date for credentials.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

| Permission type                        | Permissions (from least to most privileged) |
| :------------------------------------- | :------------------------------------------ |
| Delegated (work or school account)     | AuditLog.Read.All                           |
| Delegated (personal Microsoft account) | Not supported                               |
| Application                            | AuditLog.Read.All                           |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET https://graph.microsoft.com/beta/reports/appCredentialSignInActivities
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

If successful, this method returns a `200 OK` response code and collection of `appCredentialSignInActivities` objects in the response body.

## Examples

### Example #1: List appCredentialSignInActivities

#### Request #1

```html
GET https://graph.microsoft.com/beta/reports/appCredentialSignInActivities
```

#### Response #1

```json
HTTP/1.1 200 OK 

{
  "value": [
    {
      "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3fGFwcGxpY2F0aW9u",
      "keyId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
      "keyUsage": "sign",
      "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
      "appObjectId": "6920caa5-1cae-4bc8-bf59-9c0b8495d240",
      "servicePrincipalObjectId": "cf533854-9fb7-4c01-9c0e-f68922ada8b6",
      "resourceId": "a89dc091-a671-4da4-9fcf-3ef06bdf3ac3",
      "credentialOrigin": "application",
      "expirationDate": "2021-04-01T21:36:48-8:00",
      "signInActivity": {
        "lastSignInDateTime": "2021-03-18T00:00:00-8:00",
        "lastSignInRequestId": "guid1"
      }
    },
    {
      "id": "OGEzN2NmZWMtYjBhMS00Y2IxLWFjMDgtYzUyYjAzODM0ZjRhfHNlcnZpY2VQcmluY2lwYWw=",
      "keyId": "8a37cfec-b0a1-4cb1-ac08-c52b03834f4a",
      "keyUsage": "verify",
      "appId": "09e9da93-c1e8-4000-8b96-1ea6a12acf72",
      "appObjectId": "2e9276ec-7895-41f0-b63c-4d1d94552362",
      "servicePrincipalObjectId": "afb9dcdc-34ef-4d8e-91b5-4f094758100c",
      "resourceId": "cde0ef8b-9c88-473f-89c9-91eebafdec8b",
      "credentialOrigin": "servicePrincipal",
      "expirationDate": "2021-05-11T08:36:48-8:00",
      "signInActivity": {
        "lastSignInDateTime": "2021-02-01T01:23:46-8:00",
        "lastSignInRequestId": "guid2"
      }
    }
  ]
}

```

### Example #2: Get appCredentialSignInActivities by entity id

#### Request #2

```html
GET
https://graph.microsoft.com/beta/reports/appCredentialSignInActivities/ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3fGFwcGxpY2F0aW9u
```

#### Response #2

```json
HTTP/1.1 200 OK 

{
  "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3fGFwcGxpY2F0aW9u",
  "keyId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
  "keyUsage": "sign",
  "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
  "appObjectId": "6920caa5-1cae-4bc8-bf59-9c0b8495d240",
  "servicePrincipalObjectId": "cf533854-9fb7-4c01-9c0e-f68922ada8b6",
  "resourceId": "a89dc091-a671-4da4-9fcf-3ef06bdf3ac3",
  "credentialOrigin": "application",
  "expirationDate": "2021-04-01T21:36:48-8:00",
  "signInActivity": {
    "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
    "lastSignInRequestId": "guid1"
  }
}

```

### Example #3: Get appCredentialSignInActivities for a credential key

#### Request #3

```html
GET
https://graph.microsoft.com/beta/reports/appCredentialSignInActivities?$filter=keyId eq '83f45296-fb8f-4aaa-a399-ac51084e02b7'
```

#### Response #3

```json
HTTP/1.1 200 OK

{
  "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3fGFwcGxpY2F0aW9u",
  "keyId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
  "keyUsage": "sign",
  "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
  "appObjectId": "6920caa5-1cae-4bc8-bf59-9c0b8495d240",
  "servicePrincipalObjectId": "cf533854-9fb7-4c01-9c0e-f68922ada8b6",
  "resourceId": "a89dc091-a671-4da4-9fcf-3ef06bdf3ac3",
  "credentialOrigin": "application",
  "expirationDate": "2021-04-01T21:36:48-8:00",
  "signInActivity": {
    "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
    "lastSignInRequestId": "guid1"
  }
}

```

### Example #4: Get appCredentialSignInActivities for an application

#### Request #4

```html
GET
https://graph.microsoft.com/beta/reports/appCredentialSignInActivities?$filter=appId eq 'f4d9654f-0305-4072-878c-8bf266dfe146'
```

#### Response #4

```json
HTTP/1.1 200 OK
{
  "id": "ODNmNDUyOTYtZmI4Zi00YWFhLWEzOTktYWM1MTA4NGUwMmI3fGFwcGxpY2F0aW9u",
  "keyId": "83f45296-fb8f-4aaa-a399-ac51084e02b7",
  "keyUsage": "sign",
  "appId": "f4d9654f-0305-4072-878c-8bf266dfe146",
  "resourceId": "a89dc091-a671-4da4-9fcf-3ef06bdf3ac3",
  "credentialOrigin": "application",
  "expirationDate": "2021-04-01T21:36:48-8:00",
  "signInActivity": {
    "lastSignInDateTime": "2021-04-01T00:00:00-8:00",
    "lastSignInRequestId": "guid1"
  }
}

```

## Schema overview

### Entity types

#### appCredentialSignInActivity

A sign in activity for a credential. Contains information around usage time of the credential.

##### Properties

| Property                   | Type                           | Description                                                                                           | Key | Required | ReadOnly |
| -------------------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- | --- | -------- | -------- |
| `id`                       | `string`                       | The unique identifier of the appCredentialSignInActivity instance in the response.                    | Yes | Yes      | Yes      |
| `keyId`                    | `string`                       | The key id of the credential.                                                                         | No  | Yes      | Yes      |
| `keyUsage`                 | `enum`                         | Specifies what the key was used for; possible values are "sign" or "verify".                          | No  | Yes      | Yes      |
| `appId`                    | `string`                       | The id of the credential application.                                                                 | No  | Yes      | Yes      |
| `appObjectId`              | `string`                       | The id of the credential application instance.                                                        | No  | No       | Yes      |
| `servicePrincipalObjectId` | `string`                       | The id of the service principal.                                                                      | No  | No       | Yes      |
| `resourceId`               | `string`                       | The id of the accessed resource.                                                                      | No  | Yes      | Yes      |
| `credentialOrigin`         | `enum`                         | The type the key credential originated from; possible values are "application" or "servicePrincipal". | No  | Yes      | Yes      |
| `createdDateTime`          | `DateTimeOffset`               | The dateTimeOffset when the credential was created.                                                   | No  | Yes      | Yes      |
| `expirationDateTime`       | `DateTimeOffset`               | The dateTimeOffset the credential is set to expire.                                                   | No  | Yes      | Yes      |
| `signInActivity`           | `microsoft.graph.signInActivity` | The sign-in activity of the credential across all flows.                                              | No  | Yes      | Yes      |

##### Supported functionality

| Operation | Supported | Method        | Success | Notes |
| --------- | :-------: | ------------- | ------- | ----- |
| List      |     ✓     | `GET`         | `200`   |       |
| Get       |     ✓     | `GET`         | `200`   |       |
| Create    |     X     | `POST`        | `201`   |       |
| Update    |     X     | `PATCH`/`PUT` | `204`   |       |
| Delete    |     X     | `DELETE`      | `204`   |       |

##### Supported query patterns

| Pattern                | Supported | Syntax                                                                                             | Notes |
| ---------------------- | :-------: | -------------------------------------------------------------------------------------------------- | ----- |
| Server-side pagination |     ✓     | `@odata.nextLink`                                                                                  |       |
| Filter                 |     ✓     | `/appCredentialSignInActivities?$filter=signInActivity/lastSigninDateTime lt 2020-01-01T00:00:00Z` ||
| Filter                 |     ✓     | `/appCredentialSignInActivities?$filter=keyId eq '83f45296-fb8f-4aaa-a399-ac51084e02b7'`           ||
| Filter                 |     ✓     | `/appCredentialSignInActivities?$filter=appId eq 'f4d9654f-0305-4072-878c-8bf266dfe146'`           |       |
| OrderBy                |     ✓     | `/appCredentialSignInActivities?$orderby=signInActivity/lastSignInDateTime desc`                   ||
| OrderBy                |     ✓     | `/appCredentialSignInActivities?$orderby=expirationDate asc`                                       |       |

#### Entity type: reportRoot

##### Properties

| Property                        | Type                                           | Description                                                                                             | Key | Required | ReadOnly |
| ------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------- | --- | -------- | -------- |
| `appCredentialSignInActivities` | `Collection(self.appCredentialSignInActivity)` | The sign in activities for a credential. Contains information around last usage time of the credential. | No  | No       | Yes      |
