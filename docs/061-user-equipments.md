# User equipments

User equipments allows you to create your own connected locker .
Thanks to this, you will be able to know the usage of your equipments on 3 elements :

* Distance
* Duration
* Number of session

We provide 4 categories (shoes, bike, racquet, other).

You can link an equipment to a single or multiple sports.
A sport can only have 1 equipment by category linked (1 pair of shoes, 1 bike, or 1 racket). 
For example if you're linking an new shoes to Running, who already had a default shoes, your new one will replace the previous one.

After doing a sport activity, your activity's sum-up (Distance, Duration, Number of session) will be added to your equipment(s).


## Create a new user equipment

### Request

`POST https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments`
 

> Request Body

```json
{
    "user": "/v2/users/{userId}",
    "category": "shoes",
    "brand": "Kalenji",
    "name": "KIPRUN KS LIGHT 2",
    "startDate": "2020-06-12T09:18:00+00:00",
    "sportsAutoAssigned": [
        "/v2/sports/{sportId}"
    ]
}
```

You will need to indicated some URI ressources to create a new user equipment :

* sportsAutoAssigned refers to the URI of the sport
* user refers to the URI of your user

> Curl

```shell
curl -X POST \
  https://api.decathlon.net/sportstrackingdata/v2/user_equipments \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
    "user": "/v2/users/{userId}",
    "category": "shoes",
    "brand": "Kalenji",
    "name": "KIPRUN KS LIGHT 2",
    "startDate": "2020-06-12T09:18:00+00:00",
    "sportsAutoAssigned": [
        "/v2/sports/{sportId}"
    ]
}'
```

By giving a sport auto assigned, that means that your equipment will be automatically incremented with this sport's activities.


> Response

```
status 201 : Created
{
    "@context": "\/v2\/contexts\/UserEquipment",
    "@id": "\/v2\/user_equipments\/{equipmentId}",
    "@type": "UserEquipment",
    "id": "{equipmentId}",
    "user": "\/v2\/users\/{userId}",
    "category": "shoes",
    "brand": "KALENJI",
    "name": "KIPRUN KS LIGHT 2",
    "startDate": "2020-06-12T09:18:00+00:00",
    "sumups": [],
    "sportsAutoAssigned": [
        {
            "@id": "\/v2\/sports\/{sportId}",
            "@type": "Sport",
            "translatedNames": {
                "de": "Laufsport",
                "en": "Running",
                "es": "Carrera",
                "fr": "Course à pied",
                "hu": "Futás",
                "it": "Corsa a piedi",
                "nl": "Hardlopen",
                "pl": "Bieg",
                "pt": "Corrida",
                "ru": "Бег",
                "zh": "赛跑"
            }
        }
    ],
    "createdAt": "2019-07-19T08:44:27+00:00",
    "updatedAt": "2019-07-19T08:44:27+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


## Autocomplete 

To simplify equipment's creation we propose an autocompletion API.
You can use parameters on URL to optimize the result :

`/autocomplete/name/air?brand=NIKE`

`/autocomplete/brand/KALE?type=shoes`


> Curl

```shell
curl -X GET \
    https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments/autocomplete/brand/KAL \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
```
> Response

```shell
[
    "KALENJI"
]
```

It will propose, according to what user wrote, an existing products list (for brand and product name).

 Request

`POST https://api-global.decathlon.net/sportstrackingdata/autocomplete/brand/{caracters}`

`POST https://api-global.decathlon.net/sportstrackingdata/autocomplete/name/{caracters}`

## Get user equipments

> Curl

```shell
curl -X GET \
    https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments?user={userId} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
```



> Response

```
status 200 : Ok
{
    "@context": "\/v2\/contexts\/UserEquipment",
    "@id": "\/v2\/user_equipments",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "\/v2\/user_equipments\/{equipmentId}",
            "@type": "UserEquipment",
            "id": "{equipmentId}",
            "user": "\/v2\/users\/{userId}",
            "category": "shoes",
            "brand": "Kalenji",
            "name": "KIPRUN KS LIGHT",
            "sumups": {
                "5": 47820,
                "24": 5778,
                "98": 1
            },
    		"sportsAutoAssigned": [
                {
                    "@id": "\/v2\/sports\/{sportId}",
                    "@type": "Sport",
                    "translatedNames": {
                        "de": "Laufsport",
                        "en": "Running",
                        "es": "Carrera",
                        "fr": "Course à pied",
                        "hu": "Futás",
                        "it": "Corsa a piedi",
                        "nl": "Hardlopen",
                        "pl": "Bieg",
                        "pt": "Corrida",
                        "ru": "Бег",
                        "zh": "赛跑"
                    }
                }
            ],
            "createdAt": "2019-07-11T12:44:12+00:00",
            "updatedAt": "2019-07-11T13:31:36+00:00"
        },
        {
            "@id": "\/v2\/user_equipments\/{equipmentId}",
            "@type": "UserEquipment",
            "id": "{equipmentId}",
            "user": "\/v2\/users\/{userId}",
            "category": "shoes",
            "brand": "Kalenji",
            "name": "KIPRUN KS LIGHT",
            "sumups": {
                "5": 20000,
                "24": 95778,
                "98": 2
            },
    		"sportsAutoAssigned": [
                {
                    "@id": "\/v2\/sports\/{sportId}",
                    "@type": "Sport",
                    "translatedNames": {
                        "de": "Walking",
                        "en": "Walking",
                        "es": "Caminata",
                        "fr": "Marche",
                        "hu": "Gyaloglás",
                        "it": "Marcia",
                        "nl": "Wandelen",
                        "pl": "Chód",
                        "pt": "Marcha",
                        "ru": "Ходьба",
                        "zh": "步行"
                    }
                }
            ],
            "createdAt": "2019-07-11T14:29:18+00:00",
            "updatedAt": "2019-07-11T15:49:40+00:00"
        }
    ],
    "hydra:view": {
        "@id": "\/v2\/user_equipments?user={userId}&page=1",
        "@type": "hydra:PartialCollectionView"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "\/v2\/user_equipments{?user,user[],sportsAutoAssigned,sportsAutoAssigned[]}",
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
                "variable": "sportsAutoAssigned",
                "property": "sportsAutoAssigned",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "sportsAutoAssigned[]",
                "property": "sportsAutoAssigned",
                "required": false
            }
        ]
    }
}
status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```

## Modify user equipment
You can modify an equipment. For exemple if you want to change or add an auto assigned sport, or rename your equipment.

### Request

`PUT https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments/{equipmentId}`
 

> Request Body

```json
{
    "sportsAutoAssigned": [
        "/v2/sports/{sportId}"
    ]
}
```

> Curl

```shell
curl -X PUT \
  https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments/{equipmentId} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
  -d '{    "sportsAutoAssigned": [
        "/v2/sports/10"
    ]}'
```

Changing a auto assigned sport will not reset the equipment's sum-up. New auto assigned sport activities sum-up will be added to the previous.

> Response

```
status 200: OK
{
    "@context": "\/v2\/contexts\/UserEquipment",
    "@id": "\/v2\/user_equipments\/{equipmentId}",
    "@type": "UserEquipment",
    "id": "{equipmentId}",
    "user": "\/v2\/users\/{userId}",
    "category": "shoes",
    "brand": "KALENJI",
    "name": "KIPRUN KS LIGHT 2",
    "sumups": [],
    "sportsAutoAssigned": [
        {
            "@id": "\/v2\/sports\/{sportId}",
            "@type": "Sport",
            "translatedNames": {
                "de": "Gewichtheben",
                "en": "Weightlifting",
                "es": "Halterofilia",
                "fr": "Haltérophilie",
                "hu": "Súlyemelés",
                "it": "Sollevamento pesi",
                "nl": "Gewichtheffen",
                "pl": "Podnoszenie ciężarów",
                "pt": "Halterofilia",
                "ru": "Тяжелая атлетика",
                "zh": "举重"
            }
        }
    ],
    "createdAt": "2019-07-19T09:07:47+00:00",
    "updatedAt": "2019-07-19T09:08:42+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```

You will need to indicated some URI ressources to modify an equipment :

* sportsAutoAssigned refers to the URI of the sport


## Delete a user equipment

You can delete an equipment. Every informations, and link with activities will be dropped.

> Curl

```shell
curl -X DELETE \
  https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments/{equipmentId} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
```



> Response

```
status 204: No Content

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```

### Request

`DELETE https://api-global.decathlon.net/sportstrackingdata/v2/user_equipments/{equipmentId}`


## Link an activity with an equipment
You can link (or unlink) an activity with an equipment.
To do that, you have to edit an existing activity.
Here is an exemple of an activity (who is not link to an equipment), and I want to link it to my shoes.
 
> Request Body

```json
{
    "equipments": [
        "/v2/user_equipments/{equipmentId}"
    ]
}
```

### Request

`PUT https://api-global.decathlon.net/sportstrackingdata/v2/activities/{activityId}`

> Curl

```shell
curl -X PUT \
  https://api.preprod.decathlon.net/sportstrackingdata/v2/activities/{activityId} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
  -d '{
    "equipments": [
        "/v2/user_equipments/{equipmentId}"
    ]
}'
```

> Response

```
status 200: OK
{
    "@context": "\/v2\/contexts\/Activity",
    "@id": "\/v2\/activities\/{activityId}",
    "@type": "Activity",
    "id": "{activityId}",
    "name": "Tennis",
    "user": "\/v2\/users\/{userId}",
    "sport": "\/v2\/sports\/{sportId}",
    "userDevice": "\/v2\/user_devices\/{usrDeviceId}",
    "startdate": "2019-07-30T23:42:42+02:00",
    "duration": 3954,
    "latitude": null,
    "longitude": null,
    "elevation": null,
    "manual": false,
    "comment": null,
    "connector": "\/v2\/connectors\/{connectorId}",
    "userSession": null,
    "correctedElevation": false,
    "images": [],
    "thumbnail": "https:\/\/linkdata-ressources.geonaute.com\/sports\/121_h.jpg",
    "dataSummaries": {
        "5": 10000,
        "6": 86927,
        "9": 19227,
        "23": 1406,
        "24": 3954,
        "99": 807
    },
    "trackFlag": false,
    "datastreamFlag": false,
    "globalChallenges": [
    ],
    "availableDatatypes": [
        5,
        6,
        9,
        24,
        23,
        99
    ],
    "equipments": [
        "\/v2\/user_equipments\/{equipmentId}"
    ],
    "tags": [],
    "createdAt": "2019-07-31T09:32:15+00:00",
    "updatedAt": "2019-08-01T09:55:30+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


You can add one or many equipment on a activity. 



## Add an another equipment to an activity

If you want to modify an activity who had already an equipment linked, you must include this equipment on your body request :

```json
{
    "equipments": [
        "/v2/user_equipments/{currentEquipmentId}"
        "/v2/user_equipments/{+1EquipmentId}"
    ]
}
```
### Request

`PUT https://api-global.decathlon.net/sportstrackingdata/v2/activities/{activityId}`

You will need to indicated some URI ressources to modify your activity's equipment :

* equipments refers to the URI of the equipment



 
