---
description: Learn how the regular web app login flow works and why you should use it for regular web apps.
topics:
  - authorization-code
  - api-authorization
  - grants
  - authentication
contentType: concept
useCase:
  - secure-api
  - call-api
  - add-login
---
# Regular Web App Login Flow

Because regular web apps are server-side apps where the source code is not publicly exposed, they can use the Authorization Code Flow, which exchanges an Authorization Code for a token. Your app must be server-side because during this exchange, you must also pass along your application's Client Secret, which must always be kept secure, and you will have to store it in your client.


## How it works

![Regular Web App Login Flow Authentication Sequence](/media/articles/flows/concepts/auth-sequence-regular-web-app-login-flow.png)


1. The user clicks **Login** within the regular web application.
2. Auth0's SDK redirects the user to the Auth0 Authorization Server ([**/authorize** endpoint](/api/authentication#authorization-code-grant)).
3. Your Auth0 Authorization Server redirects the user to the login and authorization prompt.
4. The user authenticates using one of the configured login options and may see a consent page listing the permissions Auth0 will give to the regular web application.
5. Your Auth0 Authorization Server redirects the user back to the application with an authorization `code`.
6. Auth0's SDK sends this `code` to the Auth0 Authorization Server ([**/token** endpoint](/api/authentication?http#authorization-code)) along with the application's Client ID and Client Secret.
7. Your Auth0 Authorization Server verifies the code, Client ID, and Client Secret.
8. Your Auth0 Authorization Server responds with an ID Token and Access Token (and optionally, a Refresh Token).
9. Your application can use the Access Token to call an API to access information about the user.
10. The API responds with requested data.


## How to implement it

The easiest way to implement the Regular Web App Login Flow is to follow our [Regular Web App Quickstarts](/quickstart/webapp).

You can also use our [SDKs](/libraries).

Finally, you can follow our tutorials to use our API endpoints to [Add Login Using the Regular Web App Login Flow](/flows/guides/regular-web-app-login-flow/add-login-using-regular-web-app-login-flow) or [Call My API Using the Regular Web App Login Flow](/flows/guides/regular-web-app-login-flow/call-api-using-regular-web-app-login-flow).

## Keep reading

- Auth0 offers many ways to personalize your user's login experience using [rules](/rules) and [hooks](/hooks).
- [Tokens used by Auth0](/tokens)
