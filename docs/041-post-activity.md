# Add an activity

Add a sport activity to your account

### Request

`POST https://api.decathlon.net/sportstrackingdata/v2/activities`
 

## Request Body
To construct the body of our activity, you will need to describe the activity, name, startdate and furnhish some nodes of data :

* dataSummaries : The consolidated values of your activity like the average speed, the length, the distance... (required)
* datastream : The curves of values (speed,  heartrate, ...) (optional)
* locations : the GPS track (optional)


```json
{
    "name":"My workout",
    "startdate":"2018-04-19T08:28:49+02:00",
    "duration":954,
    "user":"/v2/users/{{user_id}}",
    "sport":"/v2/sports/381",
    "connector":"/v2/connectors/702",
    "location":{
    "elapsed_time":0,
    "latitude":50.638437762,
    "longitude":3.125975041,
    "elevation":0,
    "device":{
        "firmware":59,
        "model":17,
        "serial":"androidapp-f72c681e8442049956db",
        "user":"/v2/users/{{user_id}}"
    },
    "manual":"false"
    },
    "dataSummaries":{
        "6":86927,
        "9":19227,
        "5":5095,
        "24":954
    },
    "datastream":{
        "0":{
            "5":0,
            "6":0,
            "36":0
        },
        "1":{
            "5":0,
            "6":20135,
            "36":0
        },
        "2":{
            "5":24,
            "6":86927,
            "36":0
        },
        "3":{
            "5":24,
            "6":86927,
            "36":0
        },
        "4":{
            "5":32,
            "6":15752,
            "36":0
        },
        "5":{
            "5":32,
            "6":15752,
            "36":0
        },
        "6":{
            "5":42,
            "6":35303,
            "36":0
        },
        "7":{
            "5":42,
            "6":35303,
            "36":0
        },
        "8":{
            "5":52,
            "6":17334,
            "36":0
        },
        "9":{
            "5":52,
            "6":17334,
            "36":0
        },
        "10":{
            "5":65,
            "6":23206,
            "36":0
        },
        "11":{
            "5":65,
            "6":23206,
            "36":0
    }
    },
    "locations":{
        "0":{
            "latitude":50.638437762,
            "longitude":3.125975041,
            "elevation":0
        },
        "5":{
            "latitude":50.63821090457489,
            "longitude":3.125491838207934,
            "elevation":0
        },
        "11":{
            "latitude":50.63806783149301,
            "longitude":3.125056386784151,
            "elevation":0
        }
    }
}
```


> Curl

```shell
curl -X POST \
    https://api.decathlon.net/sportstrackingdata/v2/activities \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{	{
	"name":"My workout",
	"startdate":"2018-04-19T08:28:49+02:00",
	"duration":954,
	"user":"/v2/users/{{user_id}}" ... }' 
```




> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/Activity",
    "@id": "/v2/activities/eu2a8ff4b670340f5144",
    "@type": "Activity",
    "id": "eu2a8ff4b670340f5144",
    "name": "My workout",
    "user": "/v2/users/ed3a20dfabaf09ae73f6",
    "sport": "/v2/sports/381",
    "userDevice": null,
    "startdate": "2018-04-19T08:28:49+02:00",
    "duration": 954,
    "latitude": null,
    "longitude": null,
    "elevation": null,
    "manual": false,
    "comment": null,
    "connector": "/v2/connectors/702",
    "userSession": null,
    "correctedElevation": false,
    "images": [],
    "thumbnail": "https://linkdata-ressources.geonaute.com/sports/381_h.jpg",
    "dataSummaries": {
        "5": 5095,
        "6": 86927,
        "9": 19227,
        "23": 148,
        "24": 954,
        "99": 88
    },
    "tags": [],
    "trackFlag": true,
    "datastreamFlag": true,
    "globalChallenge": null,
    "availableDatatypes": [
        6,
        9,
        5,
        24,
        23,
        99,
        36
    ],
    "createdAt": "2018-06-25T08:28:18+00:00",
    "updatedAt": "2018-06-25T08:28:18+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.
```


## Some abstraction with referentials
* Each sport has an ID
...91 = fitness
...121 = running
...Etc.
* Each data has a data_type id.
...Ex : speed, distance, duration, speed max, speed min, speed average, steps, elevation ...
...24 = duration
...5 = distance
...Etc.

These abstractions allow to manipulate any sports with any data. (Tennis, running, swimming, golf, etc.)

## Limitations
* You can not POST an activity with a payload size bigger than 3 Mo.
* Activities tag can't contain special caracters (@,*;:/ for exemple) and can't not contain space. 

