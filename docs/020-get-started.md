# Get started

API for quantified self and connected products : Sport activities, statistics & body measures


## API conventions 


All data is sent and received as JSONLD

Date format : 2013-03-09T16:39:53+00:00

Date filter : ?property[after|before|strictly_after|strictly_before]=value 
Example : createdAt[after]=2018-03-19

Country codes follow the is [norme ISO 3166](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) with 2 char ( ex : FR)

Language codes follow the [norme ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) with 2 char ( ex : NL)


## API Registration


Our self service developer portal is not yet ready. First contact infra@decathloncoach.com with information :

* name of your application
* purpose of your application
* an url for the callback Oauthv2 flow authorization code
* a logo of your application

If we validate your application, you will receive :

* an api key
* a client ID and secret for login


## Swagger

You can find a Swagger UI <a href="swagger.htm" target="_blank">here</a>.


## Authentification

Sports Tracking Data is a ressource server, the identification and authorization role is assumed by *Geonaute Account* (it will be replaced during 2019 by Decathlon Login).
Geonaute Account supports Oauth V2.

Flow supported :

* Code flow

To get a client ID, contact **infra@decathloncoach.com**

### Login flow Authorization Code

Create a login button with this link: 

`https://account.geonaute.com/oauth/authorize?response_type=code&client_id=YOUR_CLIENT_ID&redirect_uri=https://YOUR_REDIRECT_URL`

After the user login, the user will be redirected to :

`https://YOUR_REDIRECT_URL?code=XXXXXXXXXX`

Collect the code on your server side and validate it with :

```shell
curl -X GET \
  'https://account.geonaute.com/oauth/accessToken?client_id=YOUR_CLIENT_ID&redirect_uri=YOUR_REDIRECT_URL&client_secret=CLIENT_ID_SECRET&code=THE_USER_CODE&grant_type=authorization_code'
``` 

You will receive an access_token in return :

```json
{
  'access_token' : 'XXXXXXXXX'
}
```

### Get JWT bearer
With the Access token you could get a JWT bearer with a validity of 15 minutes. This bearer will be required for almost all API calls to Sports Tracking Data.

```shell
curl -X GET \
  'https://account.geonaute.com/api/me?access_token=ACCESS_TOKEN'
``` 

> Answer 

```json
{
    "email": "arthur@dent.com",
    "firstName": "Arthur",
    "gender": "male",
    "birthdate": 631238400000,
    "lastName": "Dent",
    "created": 1469717300448,
    "ldid": "HERE_THE_UNIQ_ID_FOR_SPORTS_TRACKING_DATA",
    "requestKey": "HERE_THE_JWT_bearer"
}
```



### JWT payload structure

```json
{
  "iss": "account.geonaute.com",
  "exp": 1504793223,
  "iat": 1504789623,
  "ldid": "dfdc03c5bXXXX",
  "stack": "eu1",
  "firstname": "Arthur",
  "lastname": "Dent",
  "email": "arthur@dent.com",
  "gender": "Male",
  "birthdate": "1990-01-01",
  "country": "FR"
}
```

Note the *ldid* field which is the Sports Tracling Data identification. It will serve in a lot of api calls as parameter.




## Main operations

The main API operations are : 

* **Get activities** . 
* **Post activity**


## The first call

`GET https://api.decathlon.net/sportstrackingdata/v2/me/`

> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/me/ \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```



> Sample answer

```json
{
    "@context": "/v2/contexts/User",
    "@id": "/v2/users/ed3a20dfabaa09ae73f6",
    "@type": "User",
    "id": "ed3a20dfabaa09ae73f6",
    "oneId": null,
    "gender": 1,
    "roles": [
        "ROLE_USER"
    ],
    "language": "fr",
    "country": "BE",
    "imageUrl": "https://d1v3pubopekoj.cloudfront.net/prod/people/f0f31a5a71584076c6.png",
    "birthDate": "1984-07-27",
    "createdAt": "2013-03-09T16:39:53+00:00",
    "updatedAt": "2017-12-18T09:43:43+00:00",
    "scheduleDelete": null
}
```

Congratulations ! You executed your first request to know your basic settings of you user account.
Now you will be able to add sport activities and get them by API.












