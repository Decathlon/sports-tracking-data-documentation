# Referentials

Sports Tracking Data supports many sports, many units to analyse sport activities and user's measures. To allow this, Sports Tracking Data uses a lot of abstraction. It permits to add a new sport or a new unit in a referential, then the new item is usable for everyone.

This is the list of the referentials :

## Main referentials
- Datatype
- Sport

Each time you refer to a sport, you have to indicate the ressource id which refers to the referential. Example, if you create a new sport activity for an user, you will indicate the sport "/v2/sports/121" which refers to the Running.
In same manner, Datatype is the referential of each units and measures of Sports Data. Example : Distance, Duration, Speed Current, Speed average, Speed max, elevation, body weight, body height...


## Main datatypes
Here we provide a top 25 extract from datatypes referencial used to give you a preview of the list.


Id | unit | label | cumulable | recordWay 
--------- | ----------- | ----------- | ----------- | -----------
99 | Ons | Points earned | 1 | 1
24 | s | Duration | 1 | 1
5 | m | Distance | 1 | 1
23 | kcal | Calories burnt | 1 | 1
9 | m/h | Speed avg |  | 1
6 | m/h | Speed current |  | 0
18 | m | Ascent | 1 | 1
19 | m | Descent | 1 | 1
16 | m | Elevation min |  | 0
15 | m | Elevation max |  | 1
14 | m | Elevation current |  | 0
36 |  | Mode |  | 0
4 | bpm | HR avg |  | 0
7 | m/h | Speed max |  | 1
3 | bpm | HR max |  | 1
1 | bpm | HR current |  | 0
20 | bool | Lap |  | 0
17 | m | Elevation avg |  | 0
10 | steps/min | Cadence current |  | 0
177 |  | Bike trainer resistance |  | 0
207 |  | Avg Bike Trainer Resistance |  | 0
206 |  | Avg Bike Trainer Resistance |  | 1
103 | rpm | RPM avg |  | 1
101 | rpm | RPM max |  | 0
100 | rpm | RPM current |  | 0


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
176 | Alpine skiing
183 | Alternative Nordic skiing
260 | Aqua gym sessions
326 | Archery
177 | Back country skiing
335 | Badminton
10 | Basketball
381 | Bicycle
360 | BMX
264 | Bodyboarding
35 | Boxing
265 | Canoeing and kayaking
161 | Climbing
397 | Cross trainer
404 | Cross training
402 | Daily activity
79 | Dancing
91 | Fitness
13 | Football
320 | Golf
18 | Handball
168 | Hiking
20 | Hockey
401 | Home Trainer
200 | Horse riding
110 | Indoor fitness bike
98 | Indoor weight training
367 | Inline skating
405 | Jumping rope
273 | Kite surfing
366 | Land sailing
45 | Martial arts
388 | Mountain biking
153 | Mountaineering
184 | Nordic skating
114 | Nordic walking
127 | Orientation racing
340 | Padel
7 | Paragliding
109 | Pilates
385 | Road cycling
263 | Rowing
398 | Rowing machine
27 | Rugby
399 | Run & Bike
121 | Running
301 | Sailing
380 | Scooter
374 | Skateboarding
174 | Skiing
173 | Snow-shoeing
185 | Snowboarding
354 | Squash
400 | Stand up paddle boarding
296 | Surfing
274 | Swimming
358 | Table tennis
357 | Tennis
126 | Trail
395 | Treadmill
77 | Triathlon
284 | Underwater diving
32 | Volleyball
113 | Walking
280 | Wind surfing
105 | Yoga
403 | Zumba



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





