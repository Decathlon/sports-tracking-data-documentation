# User Agreement

An easy solution to store the user agreement to use your service.

__WARNING__ : once you have User Agreements on an account, if they are all rejected, the user account is deleted. If there is no anymore agreement accepted, we don't have the right to store the user data.


## Create an user agreement

You store the acceptance of your user on your service and the filename of your legal contract.

Each user agreement has a state ( accepted | pending | rejected ).


### Request

`POST https://api.decathlon.net/sportstrackingdata/v2/user_agreements`
 



> Curl

```shell
curl -X POST \
    https://api.decathlon.net/sportstrackingdata/v2/user_agreements \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
  "user": "/v2/users/#USERLDID#",
  "serviceKey": "DecathlonCoach",
  "state": "accepted",
  "filename": "legal-document-CGS-v1.1-20180808"
	}' 
```


> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserAgreement",
    "@id": "/v2/user_agreements/1",
    "@type": "UserAgreement",
    "id": 1,
    "user": "/v2/users/820d0a384a7013997f69",
    "serviceKey": "DecathlonCoach",
    "state": "accepted",
    "dateAccept": "2018-08-10T13:28:10+00:00",
    "dateRepudiation": null,
    "filename": "legal-document-CGS-v1.1-20180808",
    "createdAt": "2018-08-10T13:28:10+00:00",
    "updatedAt": "2018-08-10T13:28:10+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```


## Get the collection of User Agreement or a single ressource


You can list all the user agreements and access to specific one.

### Request

`GET https://api.decathlon.net/sportstrackingdata/v2/user_agreements`

`GET https://api.decathlon.net/sportstrackingdata/v2/user_agreements/#RESSOURCEID#`




> Curl

```shell
curl -X GET \
    https://api.decathlon.net/sportstrackingdata/v2/user_agreements \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' 
```


> Response

```
status 200 : Ok
{
    "@context": "/v2/contexts/UserAgreement",
    "@id": "/v2/user_agreements",
    "@type": "hydra:Collection",
    "hydra:member": [
        {
            "@id": "/v2/user_agreements/1",
            "@type": "UserAgreement",
            "id": 1,
            "user": "/v2/users/820d0a384a7013997f69",
            "serviceKey": "DecathlonCoach",
            "state": "accepted",
            "dateAccept": "2018-08-10T13:28:10+00:00",
            "dateRepudiation": null,
            "filename": "legal-document-CGS-v1.1-20180808",
            "createdAt": "2018-08-10T13:28:10+00:00",
            "updatedAt": "2018-08-10T13:28:10+00:00"
        }
    ]
}
status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```




## Modify an user agreement


You can modify the state of an user agreement. For example if an user wants to revoke its acceptance to the service.


### Request

`PUT https://api.decathlon.net/sportstrackingdata/v2/user_agreements/#RESSOURCEID#`
 



> Curl

```shell
curl -X PUT \
    https://api.decathlon.net/sportstrackingdata/v2/user_agreements/#RESSOURCEID# \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
  "state": "rejected"
	}' 
```


> Response

```
status 200 : OK
{
    "@context": "/v2/contexts/UserAgreement",
    "@id": "/v2/user_agreements/1",
    "@type": "UserAgreement",
    "id": 1,
    "user": "/v2/users/820d0a384a7013997f69",
    "serviceKey": "DecathlonCoach",
    "state": "rejected",
    "dateAccept": "2018-08-10T13:28:10+00:00",
    "dateRepudiation": null,
    "filename": "legal-document-CGS-v1.1-20180808",
    "createdAt": "2018-08-10T13:28:10+00:00",
    "updatedAt": "2018-08-10T13:28:10+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```
