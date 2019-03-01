# User Records

## All

These records concern the best activities on global value (datasummary)

* Distance (5)
* Average speed (9)
* Duration (24)
* Kcal (23)
* ON points (99)
* Ascent : Elevation gain (18)
* Descent : Elevation loss  (19)

## Inside activity

These records are calculated inside the activity. You could do a slow 10 km but with the best 200m of your life. We grab it and store it here. All these records are with datatype duration (24) in seconds (aka the time to complete the distance).

* distance.200m
* distance.400m
* distance.804m
* distance.1000m
* distance.1609m
* distance.3218m
* distance.5000m
* distance.10000m
* distance.21097m
* distance.42195m
* distance.80000m
* distance.100000m

## Retreive user's records

Get the collection of records.

### Request

`GET https://api-eu.decathlon.net/sportstrackingdata/v2/user_records`
 


Here we get all records for an user and specify the sport 121 (aka Running cf /v2/sports)

> Curl

```shell
curl -X GET \
    https://api-eu.decathlon.net/sportstrackingdata/v2/user_records?sport=121 \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```


> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/UserRecord",
    "@id": "/v2/user_records",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_records/1558821",
            "@type": "UserRecord",
            "id": "1558821",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/5",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 7651,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558827",
            "@type": "UserRecord",
            "id": "1558827",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/99",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 353,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558826",
            "@type": "UserRecord",
            "id": "1558826",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 2561,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558825",
            "@type": "UserRecord",
            "id": "1558825",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/23",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 538,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558824",
            "@type": "UserRecord",
            "id": "1558824",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/19",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 39,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558823",
            "@type": "UserRecord",
            "id": "1558823",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/18",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 40,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558822",
            "@type": "UserRecord",
            "id": "1558822",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/9",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 10755,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558816",
            "@type": "UserRecord",
            "id": "1558816",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.804m",
            "value": 246,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558820",
            "@type": "UserRecord",
            "id": "1558820",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.5000m",
            "value": 1654,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558815",
            "@type": "UserRecord",
            "id": "1558815",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.400m",
            "value": 116,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558817",
            "@type": "UserRecord",
            "id": "1558817",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.1000m",
            "value": 312,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558818",
            "@type": "UserRecord",
            "id": "1558818",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.1609m",
            "value": 515,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558814",
            "@type": "UserRecord",
            "id": "1558814",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.200m",
            "value": 57,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558819",
            "@type": "UserRecord",
            "id": "1558819",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.3218m",
            "value": 1044,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558802",
            "@type": "UserRecord",
            "id": "1558802",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/5",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 934,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558808",
            "@type": "UserRecord",
            "id": "1558808",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/99",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 24,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558803",
            "@type": "UserRecord",
            "id": "1558803",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/9",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 5797,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558807",
            "@type": "UserRecord",
            "id": "1558807",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 580,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558806",
            "@type": "UserRecord",
            "id": "1558806",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/23",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 37,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558804",
            "@type": "UserRecord",
            "id": "1558804",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/18",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 9,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558805",
            "@type": "UserRecord",
            "id": "1558805",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/19",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 10,
            "createdAt": "2019-01-30T20:18:54+00:00",
            "updatedAt": "2019-01-30T20:18:54+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558799",
            "@type": "UserRecord",
            "id": "1558799",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "distance.200m",
            "value": 112,
            "createdAt": "2019-01-30T20:18:53+00:00",
            "updatedAt": "2019-01-30T20:18:53+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558800",
            "@type": "UserRecord",
            "id": "1558800",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "distance.400m",
            "value": 236,
            "createdAt": "2019-01-30T20:18:53+00:00",
            "updatedAt": "2019-01-30T20:18:53+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        },
        {
            "@id": "/v2/user_records/1558801",
            "@type": "UserRecord",
            "id": "1558801",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu2511d65eadf35f5083",
            "sport": "/v2/sports/121",
            "type": "distance.804m",
            "value": 491,
            "createdAt": "2019-01-30T20:18:53+00:00",
            "updatedAt": "2019-01-30T20:18:53+00:00",
            "date": "2019-01-30T12:00:00+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/user_records?sport=121&page=1",
        "@type": "hydra:PartialCollectionView"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/user_records{?activity,activity[],sport,sport[],type,type[],order[id],order[type],order[value],order[createdAt],order[updatedAt]}",
        "hydra:variableRepresentation": "BasicRepresentation",
        "hydra:mapping": [
            {
                "@type": "IriTemplateMapping",
                "variable": "activity",
                "property": "activity",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "activity[]",
                "property": "activity",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "sport",
                "property": "sport",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "sport[]",
                "property": "sport",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "type",
                "property": "type",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "type[]",
                "property": "type",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[id]",
                "property": "id",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[type]",
                "property": "type",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[value]",
                "property": "value",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[createdAt]",
                "property": "createdAt",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[updatedAt]",
                "property": "updatedAt",
                "required": false
            }
        ]
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```


## Focus on record element

```json
{
            "@id": "/v2/user_records/1558822",
            "@type": "UserRecord",
            "id": "1558822",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/9",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "all",
            "value": 10755,
            "createdAt": "2019-01-30T20:19:53+00:00",
            "updatedAt": "2019-01-30T20:19:53+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        }
              
```

We can distinguish, five major fields :

* datatype : it is the type of record : max time, max elevation gain, max average speed (cf /v2/datatypes)
* activity : it is the ressource id of the activity which owns this record
* sport : the sport record : running, walking...
* type : All represent a record on the entire activity, the others represent a part of the activity, for example "distance.5000m" it is your best 5K
* value : it is the value of your record for example 15000 m/h for average speed in running

### A record type all
* datatype : 9 (average speed)
* sport : 121 (running)
* type : all
* value : 10755 (10,755 km/h)
* activity : eu21ec7ac76128fa6151 



## A record type distance.x

> A record type distance.5000m

```json
        {
            "@id": "/v2/user_records/1558820",
            "@type": "UserRecord",
            "id": "1558820",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/24",
            "activity": "/v2/activities/eu21ec7ac76128fa6151",
            "sport": "/v2/sports/121",
            "type": "distance.5000m",
            "value": 1654,
            "createdAt": "2019-01-30T20:19:52+00:00",
            "updatedAt": "2019-01-30T20:19:52+00:00",
            "date": "2018-11-18T12:00:00+00:00"
        }
```

* datatype : 24 (duration seconds)
* sport : 121 (running)
* type : distance.5000m
* value : 1654 (27min)
* activity : eu21ec7ac76128fa6151 


## Calculation of records

The records are calculated automatically after the import of an activity.
To delete a record, you have to modify or delete the activity attached to the record.

