# Retreive activities

Get the collection of activities.


### Request

`GET https://api-eu.decathlon.net/sportstrackingdata/v2/activities`

> Curl

```shell
curl -X GET \
    https://api-eu.decathlon.net/sportstrackingdata/v2/activities \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```


> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/Activity",
    "@id": "/v2/activities",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/activities/eu205bc29d9975f27cfb",
            "@type": "Activity",
            "id": "eu205bc29d9975f27cfb",
            "name": "Test V2 - Android - 21 juin 2018",
            "user": "/v2/users/ed3a20dfabaf09ae73f6",
            "sport": "/v2/sports/381",
            "userDevice": null,
            "startdate": "2018-06-21T09:36:03+02:00",
            "duration": 753,
            "latitude": null,
            "longitude": null,
            "elevation": null,
            "manual": true,
            "comment": null,
            "connector": null,
            "userSession": null,
            "correctedElevation": true,
            "images": [],
            "thumbnail": "https://linkdata-ressources-eu2.geonaute.com/prod/ed3a20dfabaf09ae73f6/maps/eu205bc29d9975f27cfb.png",
            "dataSummaries": {
                "5": 4127,
                "9": 19731,
                "15": 42,
                "16": 25,
                "18": 17,
                "19": 1,
                "23": 117,
                "24": 753,
                "97": 70,
                "99": 70
            },
            "tags": [],
            "trackFlag": true,
            "datastreamFlag": true,
            "globalChallenge": null,
            "availableDatatypes": [
                5,
                9,
                23,
                24,
                97,
                99,
                6,
                14
            ],
            "createdAt": "2018-06-21T08:35:36+00:00",
            "updatedAt": "2018-06-21T08:35:38+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/activities?limit=2&page=1",
        "@type": "hydra:PartialCollectionView",
        "hydra:next": "/v2/activities?limit=2&page=2"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/activities{?user,user[]}",
        "hydra:variableRepresentation": "BasicRepresentation",
        "hydra:mapping": [
            {
                "@type": "IriTemplateMapping",
                "variable": "user",
                "property": "user",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "user[]",
                "property": "user",
                "required": false
            }
        ]
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


## Filters
You could apply many filter on this request, for example an interval of date, a sport id, ...

