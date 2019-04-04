# User measures

User measures allows you to do quantified self for your body on many datatypes (weight, Body fat, height, Heart rate min, max, ...).
Each measure is dated, when you get a collection you can show the evolution of the datatype selected.

## Reminder about Datatypes

For these examples we will use the datatype 181: Weight in gramms :

`GET https://api-eu.decathlon.net/sportstrackingdata/v2/datatypes/181`

```json
{
    "@context": "/v2/contexts/Datatype",
    "@id": "/v2/datatypes/181",
    "@type": "Datatype",
    "id": 181,
    "unit": "g",
    "translatedNames": {
        "en": "Weight"
    },
    "translatedDescriptions": {
        "en": null
    },
    "recordWay": 0,
    "cumulable": false,
    "active": true,
    "createdAt": "2018-03-14T21:36:31+00:00",
    "updatedAt": "2018-03-23T10:23:55+00:00"
}
```


## Create a new user measure

### Request

`POST https://api-eu.decathlon.net/sportstrackingdata/v2/user_measures`
 

> Request Body

```json
{
  "user": "/v2/users/eu23d736c047075def68",
  "datatype": "/v2/datatypes/181",
  "value": 70000,
  "date": "2018-04-18T19:36:41.081Z"
}
```

You will need to indicated some URI ressources to create a new user measure :

* datatype refers to the unit of the measure
* user refers to the URI of your user

> Curl

```shell
curl -X POST \
    https://api-eu.decathlon.net/sportstrackingdata/v2/user_measures \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
  "user": "/v2/users/eu23d736c047075def68",
  "datatype": "/v2/datatypes/181",
  "value": 70000,
  "date": "2018-04-18T19:36:41.081Z"
}' 
```




> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserMeasure",
    "@id": "/v2/user_measures/738526",
    "@type": "UserMeasure",
    "id": "738526",
    "user": "/v2/users/eu23d736c047075def68",
    "datatype": "/v2/datatypes/181",
    "value": 70000,
    "date": "2018-04-18T19:36:41+00:00",
    "createdAt": "2019-01-30T21:12:15+00:00",
    "updatedAt": "2019-01-30T21:12:15+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


## Get user measures

> Curl

```shell
curl -X GET \
    https://api-eu.decathlon.net/sportstrackingdata/v2/user_measures?datatype=181 \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
```



> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/UserMeasure",
    "@id": "/v2/user_measures",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_measures/738525",
            "@type": "UserMeasure",
            "id": "738525",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/181",
            "value": 90000,
            "date": "2019-01-30T20:16:36+00:00",
            "createdAt": "2019-01-30T20:16:36+00:00",
            "updatedAt": "2019-01-30T20:16:36+00:00"
        },
        {
            "@id": "/v2/user_measures/738526",
            "@type": "UserMeasure",
            "id": "738526",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/181",
            "value": 70000,
            "date": "2018-04-18T19:36:41+00:00",
            "createdAt": "2019-01-30T21:12:15+00:00",
            "updatedAt": "2019-01-30T21:12:15+00:00"
        },
        {
            "@id": "/v2/user_measures/738528",
            "@type": "UserMeasure",
            "id": "738528",
            "user": "/v2/users/eu23d736c047075def68",
            "datatype": "/v2/datatypes/181",
            "value": 69042,
            "date": "2019-01-18T19:36:41+00:00",
            "createdAt": "2019-01-30T21:14:18+00:00",
            "updatedAt": "2019-01-30T21:14:18+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/user_measures?datatype=181&page=1",
        "@type": "hydra:PartialCollectionView"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/user_measures{?user,user[],date,date[],datatype,datatype[],order[id],order[value],order[date],order[dateTimezone],order[createdAt],order[updatedAt],date[before],date[strictly_before],date[after],date[strictly_after]}",
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
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date[]",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "datatype",
                "property": "datatype",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "datatype[]",
                "property": "datatype",
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
                "variable": "order[value]",
                "property": "value",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[date]",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[dateTimezone]",
                "property": "dateTimezone",
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
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date[before]",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date[strictly_before]",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date[after]",
                "property": "date",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "date[strictly_after]",
                "property": "date",
                "required": false
            }
        ]
    }
}
status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```

