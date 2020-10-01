# Share an activity

It is possible to activate public sharing of an activity.
Everyone will be able to access to the activity by API without any user security.

When you share an activity, you create a public token that you can repudiate.


## Create the public share token

Firstly, you need the URI of the activity that you want to share, example :

* "/v2/activities/eu2511d65eadf35f5083"


### Request

`GET https://api-global.decathlon.net/sportstrackingdata/v2/share_activities`
 

### Request Body

```json
{
  "user": "/v2/users/eu23d736c047075def68",
  "activity": "/v2/activities/eu2511d65eadf35f5083"
}
```


> Curl


```shell
curl -X POST \
    https://api-global.decathlon.net/sportstrackingdata/v2/share_activities \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
  "user": "/v2/users/eu23d736c047075def68",
  "activity": "/v2/activities/eu2511d65eadf35f5083"
}' 
```




> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/ShareActivity",
    "@id": "/v2/share_activities/eu244e2e987f749dbde5",
    "@type": "ShareActivity",
    "id": "eu244e2e987f749dbde5",
    "user": "/v2/users/eu23d736c047075def68",
    "activity": {
        "@id": "/v2/activities/eu2511d65eadf35f5083",
        "@type": "Activity",
        "id": "eu2511d65eadf35f5083",
        "name": "Test V2 - Android - 30 janvier 2019",
        "user": "/v2/users/eu23d736c047075def68",
        "sport": "/v2/sports/121",
        "userDevice": null,
        "startdate": "2019-01-30T12:00:00+00:00",
        "duration": 580,
        "latitude": 50.6445,
        "longitude": 3.14039,
        "elevation": 28,
        "manual": true,
        "comment": null,
        "connector": null,
        "userSession": null,
        "images": [],
        "thumbnail": "https://linkdata-ressources-eu2.geonaute.com/preprod/eu23d736c047075def68/maps/eu2511d65eadf35f5083.png",
        "dataSummaries": {
            "5": 934,
            "7": 9000,
            "9": 5797,
            "15": 37,
            "16": 27,
            "18": 9,
            "19": 10,
            "23": 37,
            "24": 580,
            "97": 24,
            "99": 24
        },
        "globalChallenge": null,
        "availableDatatypes": [
            5,
            7,
            9,
            15,
            16,
            18,
            19,
            23,
            24,
            97,
            99,
            14,
            6
        ],
        "createdAt": "2019-01-30T20:18:51+00:00",
        "updatedAt": "2019-01-30T20:18:54+00:00",
        "datastream": {
            "0": {
                "5": 0,
                "6": 4680,
                "14": 28.40039
            },
            "4": {
                "5": 5,
                "6": 4400,
                "14": 28.299805
            },
            "5": {
                "5": 6,
                "6": 4320,
                "14": 28.299805
            },
            "9": {
                "5": 11,
                "6": 5400,
                "14": 28.299805
            },
            "10": {
                "5": 13,
                "6": 5400,
                "14": 28.299805
            },
            ...
        },
        "locations": {
            "0": {
                "latitude": 50.6445,
                "longitude": 3.14039,
                "elevation": 28.40039
            },
            "4": {
                "latitude": 50.64447,
                "longitude": 3.14033,
                "elevation": 28.299805
            },
            "5": {
                "latitude": 50.64446,
                "longitude": 3.14032,
                "elevation": 28.299805
            },
            ...
        },
        "tags": null
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```

Thank to the new share URI : "/v2/share_activities/eu244e2e987f749dbde5" you will be able to get this activity.


## GET the activity 

> Curl

```shell
curl -X GET \
  https://api-global.decathlon.net/sportstrackingdata/v2/share_activities/eu244e2e987f749dbde5 \
  -H 'Accept: application/ld+json, application/json, text/html' 
  -H 'x-api-key: {your api key}' \
```

Once the share public token generated, you can GET the activity without any user security.

`GET "/v2/share_activities/eu244e2e987f749dbde5"`



