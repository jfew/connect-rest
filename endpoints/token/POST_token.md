# Token Resources

    POST token

## Description
Retrieve session tokens for a given set of application and user credentials.

***

## Parameters

- **application_key** _(required)_ — SystemId for which the token is requested.
- **application_secret** _(required)_ — SystemPassword for which the token is requested.
- **user_id** _(optional)_ — UserId for which the token is requested.
- **user_password** _(optional)_ — UserPassword for which the token is requested.
- **coordination_id** _(optional)_ - An ID unique to the request for coordination and debugging purposes.

***

## Return format
A JSON array with followed token object.

***

## Errors
All known errors cause the resource to return HTTP error code header together with a JSON array containing at least 'status' and 'error' keys describing the source of error.

- **400 Bad Request** - The request is malformed or syntactically incorrect.
- **401 Unauthorized** - The specified application and/or user credentials are not recognized.
- **404 Not Found** - The resource is not found (i.e. HTTPS only).

***

## Example
**Request**

    POST https://connect.gettyimages.com/api/token

**Return**
``` json

"token": {
    "coordination_id": "string"
    "ssl_token": "string",
    "token": "string",
    "token_duration_minutes": int,
}

```
