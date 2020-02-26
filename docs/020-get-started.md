# Get started

API for quantified self and connected products : Sport activities, statistics , body measures & equipments


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

Sports Tracking Data is a ressource server, the identification and authorization role is assumed by *Decathlon Login*.

Flow supported :

* Authorization code

To get a client ID, contact **infra@decathloncoach.com**

### Login flow Authorization Code

Create a login button with this link: 

`https://api-eu.decathlon.net/connect/oauth/authorize?client_id=YOUR_CLIENT_ID&locale=fr_FR&redirect_uri=YOUR_REDIRCT_URI&response_type=code&state=123454&scope=profile+openid+email`


After the user login, the user will be redirected to :

`https://YOUR_REDIRECT_URL?code=XXXXXXXXXX`

Collect the code on your server side and validate it. You will receive bearer in return :

```shell
curl -X POST \
  'https://api-eu.decathlon.net/connect/oauth/token?client_id=YOUR_CLIENT_ID&client_secret=CLIENT_ID_SECRET&grant_type=authorization_code&code=THE_USER_CODE&redirect_uri=https://YOUR_REDIRECT_URL' \
``` 


> Answer 

```json
{
    "access_token": "eyJhbGciOiJSUzI1NEnR5cCI6IkpXVCJ9.eyJzdWIiOiI1YWIxMjY3OC1hYzhmLTRkM2YtOTMzOC02NTJlNzkxZGMyZWEiLCJzY29wZSI6WyJwcm9maWxlIl0sImlzcyI6ImRrY29ubmVjdC5vcmciLCJkYXX2NlbnRlciI6IkVVIiwicGVyc29uaWQiOiI1MDAwMDIzNDcwMSIsImV4cCI6MTU0NTEyNjA2NCwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6IjgxOTgxMTllLWQ4YjktNDc1ZC04MTlmLWExYTQyYWQ5YzNkMCIsImNsaWVudF9pZCI6ImRrY29ubmVjdCJ9.HGNlzYh_mlAmdazSMejNd2totNYChUZ33oZUHo27L_xfWR-C_b8-IUg-MKC0w-Or6zahifqJN5y1NfNlqrsLrAWXFg-ZDAyUYgec3kQmRaFG1AgLFUjwsCvGSYcIGY41PHM0WKRENyU_oDL7bN9AjaOLe3Ob-c2BRWBQu6a5W6fmqugQ28ZFLTGDUTcIcsOdTg0DqBU82B_CjsVrK_x1gLM4y2ozkXJ_OmvCl5CjNsvaYJHKANl8gA5TQgX7IaUAwf7YNcun_rnO1k-FeYoc_OLHWIQG1UDrbDrtUUH-WQo7AE9X5BhgzXjWd1rubv703nbq6RP3BeeoeoJIDQ",
    "token_type": "bearer",
    "refresh_token": "XXX",
    "expires_in": 899,
    "scope": "XXX",
    "jti": "XXX"
}
```



## Main operations

The main API operations are : 

* **Get activities** . 
* **Post activity**


## The first call

`GET https://api-eu.decathlon.net/sportstrackingdata/v2/me/`

> Curl

```shell
curl -X GET \
    https://api-eu.decathlon.net/sportstrackingdata/v2/me/ \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```



> Sample answer

```json
{
    "@context": "/v2/contexts/User",
    "@id": "/v2/users/YOUR_LDID",
    "@type": "User",
    "id": "YOUR_LDID
    "personId": "YOUR_PERSON_ID",
    "gender": 1,
    "roles": [
        "ROLE_USER"
    ],
    "language": "fr",
    "country": "fr",
    "imageUrl": null,
    "birthDate": "1990-10-24",
    "scheduleDelete": null,
    "createdAt": "2019-03-18T13:07:02+00:00",
    "updatedAt": "2020-02-26T10:11:58+00:00",
    "monthlyActivityMail": true,
    "unit": "metric"
}
```

Congratulations ! You executed your first request to know your basic settings of you user account.
Now you will be able to add sport activities and get them by API.












