# User statistics

The user_sumups can give you consolidated statistics on period (years and months).
The user_sumups element :

* an user_id
* a sport (121 running, ...)
* a datatype (5 distance meter, ...)
* a period (2019, 201901, ...)

## Parameters

> The API accepts many parameters to reach quickly the data you want.

```
period
period[]
user,user[]
type,type[]
order[id]
order[type]
order[period]
order[value]
order[createdAt]
order[updatedAt]
period[between]
period[gt]
period[gte]
period[lt]
period[lte]
```



## Retreive user's sumups

In this example we will look for statistics on 2018 for the running sport (121)


### Request

` GET https://api.decathlon.net/sportstrackingdata/v2/user_sumups`
 

> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/user_sumups?period=2018&sport=121 \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```


> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/UserSumup",
    "@id": "/v2/user_sumups",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_sumups/5774260",
            "@type": "UserSumup",
            "id": "5774260",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/5",
            "period": "2018",
            "value": 7651,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774261",
            "@type": "UserSumup",
            "id": "5774261",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/18",
            "period": "2018",
            "value": 40,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774262",
            "@type": "UserSumup",
            "id": "5774262",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/19",
            "period": "2018",
            "value": 39,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774263",
            "@type": "UserSumup",
            "id": "5774263",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/23",
            "period": "2018",
            "value": 538,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774264",
            "@type": "UserSumup",
            "id": "5774264",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/24",
            "period": "2018",
            "value": 2561,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774265",
            "@type": "UserSumup",
            "id": "5774265",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/97",
            "period": "2018",
            "value": 353,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774266",
            "@type": "UserSumup",
            "id": "5774266",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/99",
            "period": "2018",
            "value": 353,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        },
        {
            "@id": "/v2/user_sumups/5774267",
            "@type": "UserSumup",
            "id": "5774267",
            "type": "YearlySumup",
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121",
            "datatype": "/v2/datatypes/98",
            "period": "2018",
            "value": 1,
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/user_sumups?period=2018&sport=121&page=1",
        "@type": "hydra:PartialCollectionView"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/user_sumups{?period,period[],user,user[],type,type[],order[id],order[type],order[period],order[value],order[createdAt],order[updatedAt],period[between],period[gt],period[gte],period[lt],period[lte]}",
        "hydra:variableRepresentation": "BasicRepresentation",
        "hydra:mapping": [
            {
                "@type": "IriTemplateMapping",
                "variable": "period",
                "property": "period",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[]",
                "property": "period",
                "required": false
            },
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
                "variable": "order[period]",
                "property": "period",
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
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[between]",
                "property": "period",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[gt]",
                "property": "period",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[gte]",
                "property": "period",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[lt]",
                "property": "period",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "period[lte]",
                "property": "period",
                "required": false
            }
        ]
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```

## Explaining a sumup element

```
{
            "@id": "/v2/user_sumups/5774260",
            "@type": "UserSumup",
            "id": "5774260",
            "type": "YearlySumup", //type year
            "user": "/v2/users/eu23d736c047075def68",
            "sport": "/v2/sports/121", //sport running 121
            "datatype": "/v2/datatypes/5", // Distance in meter
            "period": "2018",
            "value": 7651, // value realised so 7,6Km of running in 2018
            "createdAt": "2019-01-30T20:19:54+00:00",
            "updatedAt": "2019-01-30T20:19:54+00:00"
        }
```

