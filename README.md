# Infogile API

Infogile is a agile and versatile but still simple backend storage solution for your web, mobile or native client. The purpose of infogile is making developers build apps faster and more secure. 

Infogile is a persistence API focused on making it easy to build and *change* your data models easily and focusing on delivering business value (yeah, we're kind of boring, we actually think that's the purpose with us developers :-)

However, it's not for everyone, if you intend to collect data from IoT devices and do streaming analytics we suggest you use a better suited platform. If your app have the need to store and maintain data according to a data model and you:
1. Want to have a simple way of managing your data and data model (in runtime, mind you!)
2. Simple API 
3. Secure

# How to use the API

## Authentication
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

asd

| Tables | Are | Cool |
|----------|:-------------:|------:|
| col 1 is | left-aligned | $1600 |
| col 2 is | centered | $12 |
| col 3 is | right-aligned | $1 |
