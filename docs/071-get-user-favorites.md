# User favorites

User can save some favorites things.

* a sport
* a program 
* a session 
* an advice
* an activity



## Retreive user's favorites

### Parameters

> The API accepts many parameters to reach quickly the data you want.

```
user
user[]
type
type[]
provider
provider[]
order[id]
order[createdAt]
```


### Request

` GET https://api.decathlon.net/sportstrackingdata/v2/user_favorites`
 

> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/user_favorites \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
```


> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/UserFavorite",
    "@id": "/v2/user_favorites",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_favorites/ressource_id",
            "@type": "UserFavorite",
            "id": "ressource_id",
            "user": "/v2/users/user_id",
            "type": "program",
            "provider": "DCM",
            "value": "your_value",
            "createdAt": "2020-09-08T14:32:18+00:00",
            "updatedAt": "2020-09-08T14:32:18+00:00"
        },
        {
            "@id": "/v2/user_favorites/ressource_id",
            "@type": "UserFavorite",
            "id": "ressource_id",
            "user": "/v2/users/user_id",
            "type": "sport",
            "provider": "STD",
            "value": "your_value",
            "createdAt": "2020-09-08T15:24:51+00:00",
            "updatedAt": "2020-09-08T15:24:51+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/user_favorites?page=1",
        "@type": "hydra:PartialCollectionView"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/user_favorites{?user,user[],type,type[],provider,provider[],order[id],order[createdAt]}",
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
                "variable": "provider",
                "property": "provider",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "provider[]",
                "property": "provider",
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
                "variable": "order[createdAt]",
                "property": "createdAt",
                "required": false
            }
        ]
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```

## Create a user's favorite

### Parameters

Some elements on this API are whithelisted :

* type : program / simplesession / session / sport / advice / activity
* provider : STD / DCM

Contact us if you want to add new elements.


### Request

` POST https://api.decathlon.net/sportstrackingdata/v2/user_favorites`

> Request Body

```json
{
  "user": "/v2/users/{{ldid}}",
  "value" : "mySessionValue",
  "type" : "session",
  "provider":"DCM"
}
```

> Response

```
{
    "@context": "/v2/contexts/UserFavorite",
    "@id": "/v2/user_favorites/ressource_id",
    "@type": "UserFavorite",
    "id": "ressource_id",
    "user": "/v2/users/user_id",
    "type": "session",
    "provider": "DCM",
    "value": "mySessionValue",
    "createdAt": "2021-02-18T15:30:28+00:00",
    "updatedAt": "2021-02-18T15:30:28+00:00"
}
```

