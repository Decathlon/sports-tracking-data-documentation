# User program

You can create a sport program for your user. How it's work ?

An user create a program > this program can contain X session(s). Every time the user complete one of this session, his activity is linked to an user_session.

activity > user_session > user_program


## Create a user_program

3 informations are mandatory to create an user_program :

* user
* modelId : Your program model identifier
* current : A boolean to know if this program is used.


The basic needs :

### Request

`POST https://api-global.decathlon.net/sportstrackingdata/v2/user_programs`
 

> Request Body

```json
{
    "modelId": "XXX",
    "user": "/v2/users/{{ldid}}",
    "current": true
}
```

> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserProgram",
    "@id": "/v2/user_programs/XXX",
    "@type": "UserProgram",
    "id": "XXX",
    "modelId": "XXX",
    "userSessions": [],
    "user": "/v2/users/XXX",
    "current": true,
    "endedAt": null,
    "createdAt": "2020-04-17T08:02:53+00:00",
    "updatedAt": "2020-04-17T08:02:53+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```

## Create a program : go further
You can create your sessions in the same time.
This method will automatically create your user program and your user sessions linked to the program.

### Request

`POST https://api-global.decathlon.net/sportstrackingdata/v2/user_programs`
 

> Request Body

```json
{
    "modelId": "XXX",
    "user": "/v2/users/{{ldid}}",
    "current": true,
    "userSessions": [
        {
            "modelId": "XXX",
            "user": "/v2/users/{{ldid}}",
            "position": 1,
            "type": "string"
        },
        {
            "modelId": "XXX",
            "user": "/v2/users/{{ldid}}",
            "position": 2,
            "type": "string"
        }
    ]
}
```

> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserProgram",
    "@id": "/v2/user_programs/XXX",
    "@type": "UserProgram",
    "id": "XXX",
    "modelId": "XXX",
    "userSessions": [
        {
            "@id": "/v2/user_sessions/XXX",
            "@type": "UserSession",
            "modelId": "XXX",
            "user": "/v2/users/XXX",
            "position": 1,
            "type": "string"
        },
        {
            "@id": "/v2/user_sessions/XXX",
            "@type": "UserSession",
            "modelId": "XXX",
            "user": "/v2/users/XXX",
            "position": 2,
            "type": "string"
        }
    ],
    "user": "/v2/users/XXX",
    "current": true,
    "endedAt": null,
    "createdAt": "2020-04-17T08:13:18+00:00",
    "updatedAt": "2020-04-17T08:13:18+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.

```


## Get programs

To retrieve every programs launched by the user :
### Request

`GET https://api-global.decathlon.net/sportstrackingdata/v2/user_programs`
 

> Response

```
status 200: OK
{
    "@context": "/v2/contexts/UserProgram",
    "@id": "/v2/user_programs",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_programs/XXX",
            "@type": "UserProgram",
            "id": "XXX",
            "modelId": "XXX",
            "userSessions": [
                {
                    "@id": "/v2/user_sessions/XXX",
                    "@type": "UserSession",
                    "modelId": "XXX",
                    "user": "/v2/users/XXX",
                    "position": 1,
                    "type": "string"
                },
                {
                    "@id": "/v2/user_sessions/XXX",
                    "@type": "UserSession",
                    "modelId": "XXX",
                    "user": "/v2/users/XXX",
                    "position": 2,
                    "type": "string"
                },
                {
                    "@id": "/v2/user_sessions/XXX",
                    "@type": "UserSession",
                    "modelId": "XXX",
                    "user": "/v2/users/XXX",
                    "position": 3,
                    "type": "string"
                }
            ],
            "user": "/v2/users/XXX",
            "current": false,
            "endedAt": "2019-03-25T16:17:44+00:00",
            "createdAt": "2019-03-25T16:10:40+00:00",
            "updatedAt": "2019-03-25T16:17:44+00:00"
        }
    ],
    "hydra:view": {
        "@id": "/v2/user_programs?page=1",
        "@type": "hydra:PartialCollectionView",
        "hydra:next": "/v2/user_programs?page=2"
    },
    "hydra:search": {
        "@type": "hydra:IriTemplate",
        "hydra:template": "/v2/user_programs{?user,user[],modelId,modelId[],order[id],order[modelId],order[current],order[endedAt],order[createdAt],order[updatedAt]}",
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
                "variable": "modelId",
                "property": "modelId",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "modelId[]",
                "property": "modelId",
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
                "variable": "order[modelId]",
                "property": "modelId",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[current]",
                "property": "current",
                "required": false
            },
            {
                "@type": "IriTemplateMapping",
                "variable": "order[endedAt]",
                "property": "endedAt",
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


## Modify a program

To modify a program, exemple here, to declare that a program was finished by the user :

### Request

`PUT https://api-global.decathlon.net/sportstrackingdata/v2/user_programs/programID`
 
> Request Body

```json
{
	"current": false,
	"endedAt": "2020-04-1710:17:44+00:00"
}
```

> Response

```
status 200: OK
{
    "@context": "/v2/contexts/UserProgram",
    "@id": "/v2/user_programs/XXX",
    "@type": "UserProgram",
    "id": "XXX",
    "modelId": "XXX
    "userSessions": [
		XXX
    ],
    "user": "/v2/users/XXX",
    "current": false,
    "endedAt": "2020-04-17T10:17:44+00:00",
    "createdAt": "2019-03-25T16:10:40+00:00",
    "updatedAt": "2020-04-17T08:45:52+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.

```

## Delete a program

Delete a program will delete the program and every user_session linked.
Activities done with this program will not be deleted. The filed userSession will be set to null.

### Request

`DELETE https://api-global.decathlon.net/sportstrackingdata/v2/user_programs/programID`
 

> Response

```
status 204: No content

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.

```