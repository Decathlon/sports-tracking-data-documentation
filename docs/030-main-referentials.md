# Referentials

Sports Tracking Data supports many sports, many units to analyse sport activities and user's measures. To allow this, Sports Tracking Data uses a lot of abstraction. It permits to add a new sport or a new unit in a referential, then the new item is usable for everyone.

This is the list of the referentials :

## Main referentials
- Datatype
- Sport

Each time you refer to a sport, you have to indicate the ressource id which refers to the referential. Example, if you create a new sport activity for an user, you will indicate the sport "/v2/sports/121" which refers to the Running.
In same manner, Datatype is the referential of each units and measures of Sports Data. Example : Distance, Duration, Speed Current, Speed average, Speed max, elevation, body weight, body height...



## Example with Sport referential


A referential is read only. If you have a request to add a new item please contact the support.



`GET https://api-eu.decathlon.net/sportstrackingdata/v2/sports`
 
> Curl

```shell
curl -X GET \
    https://api-eu.decathlon.net/sportstrackingdata/v2/sports?active=1&page=1 \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \ 
```



> Response

```
status 200 :  OK
{
    "@context": "/v2/contexts/Sport",
    "@id": "/v2/sports",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/sports/7",
            "@type": "Sport",
            "id": 7,
            "translatedNames": {
                "de": "Gleitschirmfliegen",
                "en": "Paragliding",
                "es": "Parapente",
                "fr": "Parapente",
                "hu": "Siklóernyős",
                "it": "Parapendio",
                "nl": "Paragliding",
                "pl": "Paralotniarstwo",
                "pt": "Parapente",
                "ru": "Параплан",
                "zh": "滑翔伞"
            },
            "universe": "/v2/universes/1",
            "active": true,
            "createdAt": "2018-03-14T13:09:00+00:00",
            "updatedAt": "2018-08-10T04:00:07+00:00"
        },
        {
            "@id": "/v2/sports/10",
            "@type": "Sport",
            "id": 10,
            "translatedNames": {
                "de": "Basketball",
                "en": "Basketball",
                "es": "Baloncesto",
                "fr": "Basketball",
                "hu": "Kosárlabda",
                "it": "Basket",
                "nl": "Basketbal",
                "pl": "Koszykówka",
                "pt": "Basquetebol",
                "ru": "Баскетбол",
                "zh": "篮球"
            },
            "universe": "/v2/universes/2",
            "active": true,
            "createdAt": "2018-03-14T13:09:00+00:00",
            "updatedAt": "2018-08-10T04:00:07+00:00"
        },
        {
            "@id": "/v2/sports/13",
            "@type": "Sport",
            "id": 13,
            "translatedNames": {
                "de": "Fußball",
                "en": "Football",
                "es": "Fútbol",
                "fr": "Football",
                "hu": "Labdarúgás",
                "it": "Calcio",
                "nl": "Voetbal",
                "pl": "Piłka nożna",
                "pt": "Futebol",
                "ru": "Футбол",
                "zh": "足球"
            },
            "universe": "/v2/universes/2",
            "active": true,
            "createdAt": "2018-03-14T13:09:00+00:00",
            "updatedAt": "2018-08-10T04:00:08+00:00"
        },
        {
            "@id": "/v2/sports/18",
            "@type": "Sport",
            "id": 18,
            "translatedNames": {
                "de": "Handball",
                "en": "Handball",
                "es": "Balonmano",
                "fr": "Handball",
                "hu": "Kézilabda",
                "it": "Pallamano",
                "nl": "Handbal",
                "pl": "Piłka ręczna",
                "pt": "Andebol",
                "ru": "Гандбол",
                "zh": "手球"
            },
            "universe": "/v2/universes/2",
            "active": true,
            "createdAt": "2018-03-14T13:09:00+00:00",
            "updatedAt": "2018-08-10T04:00:08+00:00"
        },
        {
            "@id": "/v2/sports/20",
            "@type": "Sport",
            "id": 20,
            "translatedNames": {
                "de": "Hockey",
                "en": "Hockey",
                "es": "Hockey",
                "fr": "Hockey",
                "hu": "Jéghoki",
                "it": "Hockey",
                "nl": "Hockey",
                "pl": "Hokej",
                "pt": "Hóquei",
                "ru": "Хоккей",
                "zh": "曲棍球"
            },
            "universe": "/v2/universes/2",
            "active": true,
            "createdAt": "2018-03-14T13:09:00+00:00",
            "updatedAt": "2018-08-10T04:00:08+00:00"
        },
        ...
           ],
    "hydra:view": {
        "@id": "/v2/sports?active=1&page=1",
        "@type": "hydra:PartialCollectionView",
        "hydra:next": "/v2/sports?active=1&page=2"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/sports{?active}",
        "hydra:variableRepresentation": "BasicRepresentation",
        "hydra:mapping": [
            {
                "@type": "IriTemplateMapping",
                "variable": "active",
                "property": "active",
                "required": false
            }
        ]
    }
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```


## Main sports list

Here we provide an extract from the sport referencial to give you a preview of the sports and their IDs.


Id | Sport name
--------- | -----------
7 | Paragliding 
 10 | Basketball
 13 | Football
 18 | Handball
 20 | Hockey
 27 | Rugby 
 32 | Volleyball
 35 | Boxing
 45 | Martial arts
 77 | Triathlon 
 79 | Dancing 
 91 | Fitness 
 98 | Indoor weight training
105 | Yoga
109 | Pilates 
110 | Indoor fitness bike 
113 | Walking 
114 | Nordic walking
121 | Running 
126 | Trail 
127 | Orientation racing
153 | Mountaineering
161 | Climbing
168 | Hiking
173 | Snow-shoeing
174 | Skiing
176 | Alpine skiing 
177 | Back country skiing 
183 | Alternative Nordic skiing 
184 | Nordic skating
185 | Snowboarding
200 | Horse riding
260 | Aqua gym sessions 
263 | Rowing
264 | Bodyboarding
265 | Canoeing and kayaking 
273 | Kite surfing
274 | Swimming
280 | Wind surfing
284 | Underwater diving 
296 | Surfing 
301 | Sailing 
320 | Golf
326 | Archery 
335 | Badminton 
340 | Padel 
354 | Squash
357 | Tennis
358 | Table tennis
360 | BMX 
366 | Land sailing
367 | Inline skating
374 | Skateboarding 
380 | Scooter 
381 | Bicycle 
385 | Road cycling
388 | Mountain biking 
395 | Treadmill 
397 | Cross trainer 
398 | Rowing machine
399 | Run & Bike
400 | Stand up paddle boarding
401 | Home Trainer
402 | Daily activity
403 | Zumba 
404 | Cross training
405 | Jumping rope



## Connected products referentials

- Brand
- DeviceModel
- Firmware
- Connector

These referentials are linked to the Decathlon connected products. They allow to manage the devices and get a traceability of the model and the firmwares used.


## Other referentials

- PoiCategory : list the different categories to classify a Point of Interest
- StorageKey : list the different key allowed to store some data
- Universe : list the universes to classify the different sports





