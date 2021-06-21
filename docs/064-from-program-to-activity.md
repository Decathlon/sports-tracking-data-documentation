# From program to activity

There are 2 ways to create a program.

## Create a program without detail

`POST https://api.decathlon.net/sportstrackingdata/v2/user_programs/`

> Request Body

```json
{
   "modelId": "yourModelId",
   "user": "/v2/users/{{ldid}}",
   "current": true,
   "language": "fr",
   "provider": "DCM",
   "status": "processing",
   "preferences": {
       "week_days" : ["monday","wednesday"]
   }
}
```
 
## Create a program and session(s) at the same time

`POST https://api.decathlon.net/sportstrackingdata/v2/user_programs/`

> Request Body

```json
{
   "modelId": "yourModelId",
   "user": "/v2/users/{{ldid}}",
   "current": true,
   "language": "fr",
   "provider": "DCM",
   "status": "processing",
   "preferences": {
       "week_days" : ["monday","wednesday"],
   "userSessions": [
       {
           "modelId": "xxx",
           "userProgram": "/v2/user_programs/xxx",
           "user": "/v2/users/{{ldid}}",
           "position": 1,
           "type": "session",
           "provider": "DCM",
           "status": "pending",
           "completeDate": null,
           "scheduledDate": "2021-04-25T12:00:00+00:00"
       },
       {
           "modelId": "xxx",
           "userProgram": "/v2/user_programs/xxx",
           "user": "/v2/users/{{ldid}}",
           "position": 2,
           "type": "session",
           "provider": "DCM",
           "status": "pending",
           "completeDate": null,
           "scheduledDate": "2021-04-26T12:00:00+00:00"
       }
   ]
}
```
 
## User session on a program

User session can be part of a program, or be independante (also called simpleSession).
If you created your user sessions from your user Program (seen just previously), no need to create user Session.

Otherwise, you can create how much sessions you want and linked them to your program :


`POST 'https://api.decathlon.net/sportstrackingdata/v2/user_sessions'`

> Request Body

```json
{
           "modelId": "xxx",
           "userProgram": "/v2/user_programs/xxx",
           "user": "/v2/users/{{ldid}}",
           "position": 1,
           "type": "session",
           "provider": "DCM",
           "status": "pending",
           "completeDate": null ,
           "scheduledDate": "2021-04-25T12:00:00+02:00"
}
```


## User session without program

If you want to create an independante user Session, same thing but send userProgram to null

`POST 'https://api.decathlon.net/sportstrackingdata/v2/user_sessions'`

> Request Body

```json
{
           "modelId": "xxx",
           "userProgram": null,
           "user": "/v2/users/{{ldid}}",
           "position": 1,
           "type": "simpleSession",
           "provider": "DCM",
           "status": "pending",
           "completeDate": null ,
           "scheduledDate": "2021-04-25T12:00:00+02:00"
}
```


## Create an user session from an activity

You can also create a session directly from your activity’s creation :

`POST 'https://api.decathlon.net/sportstrackingdata/v2/activities'`

> Request Body

```json
{
   "name": "Mon activité",
   "startdate": "2021-04-22T09:09:27+00:00",
   "duration": 3000,
   "user": "/v2/users/{{ldid}}",
   "sport": "/v2/sports/381",
   "userSession":{
           "modelId": "test",
           "userProgram": null,
           "user": "/v2/users/{{ldid}}",
           "type": "session",
           "provider": "DCM"
   }
}
```


## Create an activity and link to an exisiting user session

As seen just above, you can create an activity and user Session at the same time.
You can also create an activity and link it to an already existing user session :

`POST 'https://api.decathlon.net/sportstrackingdata/v2/activities'`

> Request Body

```json
{
   "name": "Mon activité",
   "startdate": "2021-04-22T07:51:19+00:00",
   "duration": 3000,
   "user": "/v2/users/{{ldid}}",
   "sport": "/v2/sports/381",
   "userSession":"/v2/user_sessions/yourUserSessionId"
}
```

## Relations between session and activity
You can link multiple activities to the same user session :
Relation N:1.
User session has a field completeDate who is automatically completed by the first activity’s startdate linked. You can update it with a PUT userSession if needed.


