# Create a device

To create a sport activity, you have two manners to declare it :

- manual creation : useful for an activity created by a form or a third app.
- With a device and a connector : Useful for an activity created by a Decathlon product to allow the traceability


This page shows you how to create a new device for an user.



### Request

`POST https://api-global.decathlon.net/sportstrackingdata/v2/user_devices`
 
> Request body 

```json
{
  "serial": "serialnumber123456",
  "model": "/v2/device_models/1",
  "firmware": "/v2/firmware/1",
  "user": "/v2/users/{{user_id}}",
  "ownership": 0,
  "lastConnectedAt": "2018-04-16T16:05:11.896Z"
}
```

You will need to indicated some URI ressources to create a new device :

- model refers to an URI of the DeviceModel Referential
- firmware refers to an URI of the Firmware Referential
- user refers to the URI of your user

> Curl

```shell
curl -X POST \
    https://api-global.decathlon.net/sportstrackingdata/v2/user_devices \
  -H 'Authorization: Bearer {your bearer}' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {your api key}' \
  -d '{
  "serial": "serialnumber123456",
  "model": "/v2/device_models/1",
  "firmware": "/v2/firmware/1",
  "user": "/v2/users/{{user_id}}",
  "ownership": 0,
  "lastConnectedAt": "2018-04-16T16:05:11.896Z"
  }' 
```




> Response

```
status 201 : Created
{
    "@context": "/v2/contexts/UserDevice",
    "@id": "/v2/user_devices/eu271ed863164e25fb3d",
    "@type": "UserDevice",
    "id": "eu271ed863164e25fb3d",
    "serial": "serialnumber123456",
    "model": "/v2/device_models/1",
    "firmware": "/v2/firmware/1",
    "user": "/v2/users/820d0XXXXXa7013969",
    "ownership": 0,
    "lastConnectedAt": "2018-04-16T16:05:11+00:00",
    "createdAt": "2018-08-17T09:35:13+00:00",
    "updatedAt": "2018-08-17T09:35:13+00:00"
}

status 4xx : Client errors, check response for details.

status 5xx : Server errors, check response for details.


```

Thank to the new device URI : "/v2/user_devices/eu271ed863164e25fb3d" you will be able to create a new sport activity linked to this device.

Please refer to the swagger to see how to list all devices for an user, how to update a device for example if the firmware is updated.


## Serial number of the device
Generally, the serial come from :

- the real serial number of the product (ex: 1CD2071D-1440-4E5F-8C23-446D3B9B )
- on the smartphones , a string composed by the os and the user id  (ex : androidapp-e615fb7b-839a-4e65-98)

We recommend these characters :
a-z A-Z 0-9 - 


## Memo : why the device management is important

- each device is unique with its serial number
- each device could have specific configuration and settings (with user_device_setting)
- each device is linked to a model id (=> check the product of the user)
- each device is linked to a firmware (=> check the software of the product)

=> So it is important for troubleshooting when a problem occurs. 

