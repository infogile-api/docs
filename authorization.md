# Authentication and Authorization
Since infogile isn't intendended to work standalone we don't keep a user registry with passwords, we merely validate other authentications using OAuth2. You determine which users (by email) have access to your AppSpaces and then use any authentication provider such as Google, Auth0, Facebook, Microsoft Live or similar.

Currently supported authentication providers:
1. Google

To call Infogile's API, you need to pass the OAuth2 `Access Token` as a Bearer token in each HTTP request header. Additionally you must provide the identity provider.
````
Authorization: Bearer <your access token>
IdentityProvider: <identity provider code>
````
Valid Identity Providers are:

| Provider | Code |
|--------|:--------|
| Google | `google` |

