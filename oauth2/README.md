Authentication in Getty Connect Using OAuth 2.0
===============================================
The Getty Connect API uses OAuth 2.0 to authenticate and authorize client applications. An application must supply a valid access token in order to request any resource in the Connect API. This access token is generated when your end user grants access to Connect API resources to your application on behalf of their Getty Images user account. Access tokens are valid for 30 minutes, after which time they need to be refreshed.

Getting Access Tokens for Single-User Integrations
--------------------------------------------------
If your application uses a single user account for all requests, you won't need to follow the same OAuth authentication process required for a normal end-user scenario described below. You can consume the API's /token resource directly by POSTing the desired application and user credentials to retrieve your access token. This is also the recommended way of generating access tokens during development of your application, regardless of whether or not your are building a single-user or multi-user integration with Connect.

Getting Access Tokens for Multi-User Integrations
-------------------------------------------------
Getty Connect supports two OAuth2-based authentication flows: Server (authorization code) and Client (implicit grant). Server flow is best for web applications when an access token will be stored server-side. Client flow is best for desktop and mobile applications, when user info will be stored on the end user's device.

### Assumptions
These instructions assume that your Connect client application has already been registered by Getty Images Connect and has an assigned API key and API secret. Check the Getty Connect developer portal for your application credentials.

### Server Authentication
This authentication flow is used when your application's end user is accessing the app for the first time with their Getty Images user credentials. It is made up of two main steps:

1. Your application makes an authorization request and gets back an authorization code.
2. Your application requests an access token, exchanging the authorization code for an access token.

Your application, end user and Getty Images' authorization server interact as follows:

FLOW DIAGRAM HERE

1. The Getty Images user opens your application for the first time.
2. Your application directs the user to the Getty Images Connect authorization page.
3. Your end user authenticates with their Getty Images user credentials and grants your application access to Connect on their behalf.
4. The authorization page redirects the user back to your application, using a redirect URI you provide. The authorization code is appended to the redirect URI's query string (assuming your end user granted access to your application).
5. Your application then exchanges the authorization code for an access token that will be used in all API requests made on your end user's behalf.

#### Authorization Request
The authorization request calls the authorize endpoint via HTTP GET:

	https://connect.gettyimages.com/oauth2/authorize?
	response_type=code&client_id=XN0IGJjaCBwaG90byBsaWJyYXJ&
	redirect_url=https%3A%2F%2Fwww.example.com

| Field         | Values      				| Use          | Description                                             					|
|:--------------|:--------------------------|:-------------|:---------------------------------------------------------------------------|
| response_type	| code        				| Required     | Tells the authentication server to follow the server authentication flow. 	|
| client_id		| API key     				| Required     | Identifies the application making the request for access.				 	|
| redirect_uri	| your encoded redirect URI | Required     | Tells the authentication server where to proceed after access is granted. 	|

#### Authorization Response
If the end user grants access to your application, the authorization server returns an authorization code and appends it to the specified redirect_uri before redirecting.

| Field | Description                                             														|
|:------|:--------------------------------------------------------------------------------------------------------------|
| code	| Unique authorization code generated for the request; must be exchanged for an access code within 10 minutes.	|
| error	| Error label and description for failed authorization requests.												|

The response returns the redirect URL with authorization code appended, which your application can use to redirect your user through the rest of the auth flow.

#### Error Codes
| Code 	| Message														| Description                                             					|
|:------|:--------------------------------------------------------------|:--------------------------------------------------------------------------|
| -		| access_denied													| Authorization server rejects the request.	|
| -		| invalid_request												| Missing, unsupported or malformed request parameter.	|
| -		| unauthorized_client											| Client is not authorized to request an auth code using this method.	|
| -		| The client_id <client_id> is not valid or has been disabled.	| Invalid client ID; returned after user submits credentials.	|
| -		| A client_id parameter must be supplied.						| Missing client ID in request.	|
| -		| A valid response_type must be supplied. 						| Missing or invalid response type.	|
| -		| A redirect_uri parameter must be supplied. 					| Redirect URI not specified.	|
| -		| Invalid redirect 												| Redirect URI is not a valid URI.	|

### Client Authentication
For applications that store user information and access tokens locally on the user's device, client authentication is the preferred OAuth flow. 

