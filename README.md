# Infogile API

Infogile is a agile and versatile but still simple backend storage solution for your web, mobile or native client. The purpose of infogile is making developers build apps faster and more secure. 

Infogile is a persistence API focused on making it easy to build and *change* your data models easily and focusing on delivering business value (yeah, we're kind of boring, we actually think that's the purpose with us developers :-)

However, it's not for everyone, if you intend to collect data from IoT devices and do streaming analytics we suggest you use a better suited platform. If your app have the need to store and maintain data according to a data model and you:
1. Want to have a simple way of managing your data and data model (in runtime, mind you!)
2. Simple API 
3. Secure

# Introduction
To be able to use Infogile's API you need to authenticate and you need to under stand the definition of objects and how
data is represented. Follow links to read more.

- [Model](concepts/model.md)
- [Authorization](authorization.md)


# The API
## Get user info
Once a user is authenticated using an authentication provider, you may need to get user's information.

````
Endpoint: /auth/userinfo
Method:   POST
````

Example
````
curl -X POST http://infogile.io/auth/userinfo \
  -H 'Authorization: Bearer <your access token>'
  -H 'IdentityProvider: <your identity provider>' 
````

## Check if the user is logged in
````
Endpoint: /auth/validlogin
Method:   GET
````

Returns
````json5
{
  "identity": "<the user's email address>",
  "givenName": "<User's given (first) name>",
  "familyName": "<User's family (last) name>",
  "email": "<User's email>",
  "createdDate": "<date the user was created>",
  "lastModifiedDate": "<date the user was last modified>",
  "enabled": <true|false>, // If the user is enabled or not,
  "status": null,
  "accessToken": "ya29.GmMxB8AEzh8NiuMopEBYmUXUqGfdJCiOnb_ZLRHNUwIulRtATg_9hQLXvZfuyzchaAierJstRp7upTHZPxrtVyw8_endkWzMeNL8QL1LnDDALTqDTt9lef_3Ct247Vt76LLxRY4",
  "identityProvider": "google"}
````

Example
````
curl -X GET http://infogile.io/auth/validlogin \
  -H 'Authorization: Bearer <your access token>'
  -H 'IdentityProvider: <your identity provider>' 
````

## List AppSpaces
To list all AppSpaces a user have access to (a user identified by their email)

````
Endpoint: /auth/appspaces
Method:   GET 
````

Returns
````json5
[
  {
    "appSpace": {
      "identity": "c0be0e4d746484b97a13bbc6d2872e9c8",
      "name": "Work order management",
      "description": "AppSpace for the Work Order Management System",
      "public": false,
    },
    "access": [ "EDIT", "USE", "ADMIN"],
  },
  {
    "appSpace": {
      "identity": "kdf78dkfjaiodfl9f09sdjd9fe2wrdbsy",
      "name": "Challenge App", 
      "description": "AppSpace for the Challenge App",
      "public": false,
    },
    "access":[ "EDIT" , "USE" , "ADMIN" ],
  }
]
````

## List Object Definitions
````
Endpoint: /api/objectdefinition/<appspace identity>
Method:   GET
````

Returns:
````json5
[
  {
    "apiName": "user",
    "identity": "USER-OBJECT-DEFINITION",
    "name": "User",
    "fields": [
      {
        "apiName": "name",
        "identity": "NAME-FIELD",
        "name": "Name",
        "fieldType": "ValueField",
        "mandatory": false,
        "systemReadonly": true,
        "systemObject": true,
        "type": "Text"
      },
      {
        "apiName": "email",
        "identity": "EMAIL-FIELD",
        "name": "Email",
        "fieldType": "ValueField",
        "mandatory": false,
        "systemReadonly": true,
        "systemObject": true,
        "type": "Text"
      },
      {
        "apiName": "userType",
        "identity": "USER-TYPE-FIELD",
        "name": "User type",
        "fieldType": "ReferenceField",
        "mandatory": false,
        "multiplicity": "OneToMany",
        "referencedType": "userType"
      }
    ]
  },
  {
    "apiName": "userType",
    "identity": "USER-TYPE",
    "name": "User type",
    "fields": [
      {
        "apiName": "name",
        "identity": "USER-TYPE-NAME",
        "name": "Name",
        "fieldType": "ValueField",
        "mandatory": false,
        "systemReadonly": false,
        "systemObject": true,
        "type": "Text"
      }
    ]
  }
]
````