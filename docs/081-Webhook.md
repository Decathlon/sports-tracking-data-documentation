# Webhook

We support a webhook system on the event of an activity create ("activity_create").
For a user, if you create a webhook to an URL that you manage, you will receive POST request with the user id and activity id every time an activity is added for this user.


## Create a webhook


### Request

`POST https://api-eu.decathlon.net/sportstrackingdata/v2/user_web_hooks`
 


> Curl

```shell
curl -X POST \
    https://api-eu.decathlon.net/sportstrackingdata/v2/user_web_hooks \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
    "user": "/v2/users/#USER_ID#",
    "url": "https://XXXXXXX.com/webhook_callback",
    "events": [
        "activity_create"
    ]
    }' 
```


> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserWebHook",
    "@id": "/v2/user_web_hooks/euXf9507eXXXXX997707",
    "@type": "UserWebHook",
    "id": "euXf9507eXXXXX997707",
    "user": "/v2/users/#USER_ID#",
    "url": "https://XXXXXXX.com/webhook_callback",
    "events": [
        "activity_create"
    ],
    "createdAt": "2019-03-18T21:23:50+00:00",
    "updatedAt": "2019-03-18T21:23:50+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```


## Format of the POST message


```json
{
    "user_id":"user_id",
    "event":{
        "name":"activity_create",
        "ressource_id":"activity_id",
        "event_time":1552944296
        }
}
```


The equivalent request made by Sports Tracking Data to your webhook url with HTTP Code 200 .

> Curl

```shell
curl -X POST \
  https://XXXXXXX.com/webhook_callback \
  -d '{"user_id":"user_id","event":{"name":"activity_create","ressource_id":"activity_id","event_time":1552944296}}'
```

## Automatic purge

To manage users who deleted their accounts on client side, a mecanism of purge is set :
If client server side response is different than 2xx since more than 5 days, with minimum 3 consecutive times, the webhook will be deleted.
