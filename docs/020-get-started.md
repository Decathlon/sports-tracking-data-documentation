
# Get started

API for quantified self and connected products : Sport activities, statistics , body measures & equipments

## API Registration

<img src="https://tempdecathloncoachinfo.s3.eu-central-1.amazonaws.com/API_subscription_steps.png" alt="planview" style="width: 700px;"/>

**You want to use our API ? First filled** [this form](https://forms.gle/4WKN7ihQBpyzMt389) :



If we validate your request, you will receive :

* an api key
* a client ID and secret for login


## Swagger

You can find a Swagger UI <a href="swagger.htm" target="_blank">here</a>.


## Endpoints and stacks

We have two major stacks, one in Europe (the default) and one in China (dedicated to the Chinese users).
The default endpoint is : 
https://api.decathlon.net/sportstrackingdata/v2/
You can also specify the Europe stack by adding a prefix "eu2" : 
https://api.decathlon.net/sportstrackingdata/eu2/v2/sports.json

To reach the Chinese stack, add the prefix cn1 : 
https://api.decathlon.net/sportstrackingdata/cn1/v2/



## API conventions 


All data is sent and received as JSONLD

Date format : 2013-03-09T16:39:53+00:00

Date filter : ?property[after|before|strictly_after|strictly_before]=value 
Example : createdAt[after]=2018-03-19

Country codes follow the is [norme ISO 3166](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) with 2 char ( ex : FR)

Language codes follow the [norme ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) with 2 char ( ex : NL)


## Quota and rate-limiting

By default, we apply :
* 100k api calls per day
* 1k maximum burst calls/minute


## Authentification

Sports Tracking Data is a ressource server, the identification and authorization role is assumed by *Decathlon Login*.
Full documentation about Decathlon Login available <a href="https://dktunited.github.io/dktconnect-login-doc/index.html" target="_blank">here</a>.


Flow supported :

* Authorization code


### Login flow Authorization Code

Create a login button with this link: 

`https://api.decathlon.net/connect/oauth/authorize?client_id=YOUR_CLIENT_ID&locale=fr_FR&redirect_uri=YOUR_REDIRCT_URI&response_type=code&state=123454&scope=profile+openid+email+sports_tracking_data`

To be able to log-in you will need to create an application to use Decathlon Login : https://dktunited.github.io/dktconnect-login-doc/ 

If you want to be able to write data you will need to add the scope : sports_tracking_data:write



After the user login, the user will be redirected to :

`https://YOUR_REDIRECT_URL?code=XXXXXXXXXX`

Collect the code on your server side and validate it. You will receive bearer in return :

```shell
curl -X POST \
  'https://api.decathlon.net/connect/oauth/token?client_id=YOUR_CLIENT_ID&client_secret=CLIENT_ID_SECRET&grant_type=authorization_code&code=THE_USER_CODE&redirect_uri=https://YOUR_REDIRECT_URL' \
``` 


> Answer 

```json
{
    "access_token": "your_acces_token",
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

`GET https://api.decathlon.net//sportstrackingdata/v2/me/`

> Curl

```shell
curl -X GET \
    https://api.decathlon.net//sportstrackingdata/v2/me/ \
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