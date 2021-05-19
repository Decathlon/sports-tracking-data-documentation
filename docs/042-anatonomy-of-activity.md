# Anatomy of an activity

In this part we describe the components of an activity.

### Request

`GET https://api.decathlon.net/sportstrackingdata/v2/activities/{{ACTIVITY_TOKEN}}`
 


> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/activities/{{ACTIVITY_TOKEN}} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}'
```



> Response

```
status 200 : OK
{
    "@context": "/v2/contexts/Activity",
    "@id": "/v2/activities/eu2cbe4bbb24082fd9ad",
    "@type": "Activity",
    "id": "eu2cbe4bbb24082fd9ad",
    "name": "Biking 2019-02-12 14:07",
    "user": "/v2/users/820d0XXXXXa7013969",
    "sport": "/v2/sports/381",
    "userDevice": null,
    "startdate": "2019-02-12T14:07:33+00:00",
    "duration": 8311,
    "latitude": 50.741407871246,
    "longitude": 3.2376379240304,
    "elevation": 35,
    "manual": true,
    "comment": null,
    "connector": null,
    "userSession": null,
    "correctedElevation": true,
    "images": [],
    "thumbnail": "https://linkdata-ressources-eu2.geonaute.com/prod/820d0XXXXXa7013969/maps/eu2cbe4bbb24082fd9ad.png",
    "dataSummaries": {
        "3": 159,
        "4": 122,
        "5": 18375,
        "7": 31554,
        "9": 12798,
        "11": 53,
        "13": 81,
        "15": 65,
        "16": 15,
        "18": 114,
        "19": 119,
        "23": 680,
        "24": 8311,
        "97": 435,
        "99": 435
    },
    "trackFlag": true,
    "datastreamFlag": true,
    "globalChallenge": null,
    "availableDatatypes": [
        3,
        4,
        5,
        7,
        9,
        11,
        13,
        23,
        24,
        97,
        99,
        18,
        19,
        16,
        15,
        20,
        1,
        10,
        6,
        14
    ],
    "createdAt": "2019-02-28T14:01:37+00:00",
    "updatedAt": "2019-02-28T14:01:40+00:00",
    "datastream": {
        "18": {
            "1": 117,
            "5": 0,
            "6": 4705,
            "10": 0,
            "14": 35,
            "20": 1
        },
        "19": {
            "1": 117,
            "5": 1.90784933,
            "6": 5684,
            "10": 0,
            "14": 35
        },
        "21": {
            "1": 117,
            "5": 6.143301449999999,
            "6": 7416,
            "10": 0,
            "14": 34.600586
        },
        
        // .... //

        "8308": {
            "1": 129,
            "5": 18375.077684660002,
            "6": 6152,
            "10": 0,
            "14": 30.799805
        },
        "8311": {
            "1": 130,
            "5": 18375.148398160003,
            "6": 0,
            "10": 0,
            "14": 30.799805
        }
    },
    "locations": {
        "18": {
            "latitude": 50.74140787124634,
            "longitude": 3.237637924030423,
            "elevation": 35
        },
        "19": {
            "latitude": 50.74142279103398,
            "longitude": 3.237651251256466,
            "elevation": 35
        },
        "21": {
            "latitude": 50.74145246297121,
            "longitude": 3.237688886001706,
            "elevation": 34.600586
        },
        
        // .... //

        "8308": {
            "latitude": 50.74317938648164,
            "longitude": 3.2363532297313213,
            "elevation": 30.799805
        },
        "8311": {
            "latitude": 50.7431798055768,
            "longitude": 3.2363539841026068,
            "elevation": 30.799805
        }
    },
    "tags": []
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


## Zoom on descriptive fields

We find here all the field to basically describe the activity.

```json
{
    "@context": "/v2/contexts/Activity",
    "@id": "/v2/activities/eu2a32c58982e074eb4a",
    "@type": "Activity",
    "id": "eu2a32c58982e074eb4a",
    "name": "Course à pied - 02/01/2020",
    "user": "/v2/users/dfdc03c5bcddd459f170", // sport of the activity
    "sport": "/v2/sports/121", // sport of the activity
    "userDevice": null, // Decathlon user device id, required if the activity is not manual
    "startdate": "2020-01-02T12:29:46+01:00", // datetime of the start of the activity
    "duration": 4008, // total duration in seconds
    "latitude": 50.6292217, //first GPS points if exists
    "longitude": 3.06597,
    "elevation": 28.600586,
    "manual": false, // the activity is considered as manual when there is no Decathlon device declared
    "comment": null, // user comment on his activity
    "connector": "/v2/connectors/801", // Decathlon Connector id, required if the activity is not manual
    "userSession": null, // Id of an userSession when the activity is linked to coaching content
    "correctedElevation": true, // internal flag when the elevation is corrected by satelite data
    "images": [], //collection of url images added to the activity
    "thumbnail": "https://XXXXXX", // thumbnail generated
    "trackFlag": true, // is the activity has a GPS track
    "datastreamFlag": true, // is the activity has a dataStream
    "globalChallenges": [], // if linked to a Decathlon global challenge
    "equipments": [], // equipments used during the activity
    "tags": [], // collection of user tag attached to the activity
    "createdAt": "2020-01-06T09:15:31+00:00",
    "updatedAt": "2020-01-06T09:15:33+00:00"
}
```

## Zoom on dataSummaries

The dataSummaries are the data consolidated for the activity. You can store here for the whole activity different type of datatype :

* total (duration, distance, kcal...)
* average (speed average, Heart rate ...)
* minimum (altitude, ...)
* maximum (altitude, speed...)


```json
{
    "dataSummaries": {
        "3": 159,
        "4": 122,
        "5": 18375, // total distance 18375 meters
        "7": 31554,
        "9": 12798, // average speed of 12.798 km/h
        "11": 53,
        "13": 81,
        "15": 65,
        "16": 15,
        "18": 114,
        "19": 119,
        "23": 680, // total kcal 680
        "24": 8311,
        "97": 435,
        "99": 435
    }
}
```

## Zoom on availableDatatypes

This node declares all the datatypes used in the dataSummary or in the datastream.

```json
{
    "availableDatatypes": [
        3,
        4,
        5,
        7,
        9,
        11,
        13,
        23,
        24,
        97,
        99,
        18,
        19,
        16,
        15,
        20,
        1,
        10,
        6,
        14
    ]
}
```

## Zoom on datastream

The datastream is a vector depending to the elapsed_time (t0 = 0sec) with all the values which can be displayed as curves or timestamped event during the activity.


In the datastream we support all the datatypes supported (please refer to /v2/datatypes).

```json
{
    "datastream": {
        "18": { //first measure at 18 seconds
            "1": 117, // current heart rate
            "5": 0, // 0 meters achieved
            "6": 4705, // 4,705 Km/h of current speed
            "10": 0,
            "14": 35,
            "20": 1 // a lap is declared here (as a boolean)
        },
        "19": {
            "1": 117,
            "5": 1.90784933,
            "6": 5684,
            "10": 0,
            "14": 35
        },
        "21": {
            "1": 117,
            "5": 6.143301449999999,
            "6": 7416,
            "10": 0,
            "14": 34.600586
        },
        
        // .... //

        "8308": {
            "1": 129,
            "5": 18375.077684660002,
            "6": 6152,
            "10": 0,
            "14": 30.799805
        },
        "8311": {
            "1": 130,
            "5": 18375.148398160003,
            "6": 0,
            "10": 0,
            "14": 30.799805
        }
    }
}
```

## Zoom on locations

The locations stream is a vector depending to the elapsed_time (t0 = 0sec) with all the GPS coordinates to display the track of the user.

If the activity is stationary the node should be empty ("locations": {})


```json
{
    "locations": {
        "18": {// first GPS point at 18 sec
            "latitude": 50.74140787124634,
            "longitude": 3.237637924030423,
            "elevation": 35
        },
        "19": {
            "latitude": 50.74142279103398,
            "longitude": 3.237651251256466,
            "elevation": 35
        },
        "21": {
            "latitude": 50.74145246297121,
            "longitude": 3.237688886001706,
            "elevation": 34.600586
        },
        
        // .... //

        "8308": {
            "latitude": 50.74317938648164,
            "longitude": 3.2363532297313213,
            "elevation": 30.799805
        },
        "8311": {
            "latitude": 50.7431798055768,
            "longitude": 3.2363539841026068,
            "elevation": 30.799805
        }
    }
}
```

## GPX, TCX and FIT compatibility

You can also get an activity in GPX, TCX or FIT format.

> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/activities/{{ACTIVITY_TOKEN}} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Accept: application/gpx+xml' \
  -H 'x-api-key: {your api key}'
```


> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/activities/{{ACTIVITY_TOKEN}} \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Accept: application/tcx+xml' \
  -H 'x-api-key: {your api key}'
```


> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/activities/{{ACTIVITY_TOKEN}}.fit \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Accept: application/octet-stream' \
  -H 'x-api-key: {your api key}'
```


### Header accept for GPX

`Accept: application/gpx+xml`



### Header accept for TCX

`Accept: application/tcx+xml`


### Header accept for FIT

`Accept: application/octet-stream`


### Example to post an activity fit file

> Curl

```shell
curl -X POST \
    https://api.decathlon.net/sportstrackingdata/v2/activities \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/octet-stream' \
  -H 'x-api-key: {your api key}'
  –data-binary 'your_fit_file'
```
