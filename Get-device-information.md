#### Brief description:

- Get information about one or more devices.


#### Request URL:

- https://SERVER_URL/api/open/v1/common/getIotInfo

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |time stamp   |
|iotIdList |No  |Array&lt;long&gt; | The device ID array that needs to be passed. If this parameter is not passed, all the devices information will be returned.  |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2SSbf0ih",
	"time": 1613693307796,
	"iotIdList": [10044,10074]
}
```

**Response JSON:**

```
{
  "code" : 0,
  "iotList" : [ {
    "iotId" : 10044,
    "name" : "SD0000004",
    "address" : "Huangdao District, Qingdao",
    "longitude" : 120.132349,
    "latitude" : 35.992877,
    "errorStatus" : "ERROR",
    "defaultProgramId" : 13,
    "isOnline" : 0,
    "machineType" : "NTUNNEL_1",
    "programId" : [ 13 ],
    "infoImg" : "https://file.cheyoudaren.com/files/carWasher/3c4fbd4336c942399e5545312a523179"
  }, {
    "iotId" : 10074,
    "name" : "Rollover car washer 1-01",
    "address" : "Qingdao",
    "longitude" : 120.102737,
    "latitude" : 36.018591,
    "errorStatus" : "ERROR",
    "defaultProgramId" : 31,
    "isOnline" : 1,
    "machineType" : "NFULL_AUTO_1",
    "programId" : [ 31, 32 ]
  } ]  
}
```

**Error example:**

```
{
  "code" : 20005,
  "msg" : "IotId does not exist"
}
```

#### Return Parameter Description:

|Parameter name|Type|Illustration|
|:-----  |:-----|-----                           |
|code |int   |Error ID. when the value is 0, there is no error.  |
|msg |String   |Error message. When the code is not 0, this field prompts the specific error reason.|
|iotList |Array   |Device information array|
|iotId |long   |Machine ID|
|name |String   |Machine Name|
|country|String   |Host country|
|address |String   |Device address|
|lng|double   |Longitude of location|
|lat|double   |Latitude of location|
|errorStatus |String   |Error status, enumeration and fields are shown in the following table.If the device has reported an error and has not handled it, the device is in the error state.A device with an error status does not mean that the device is not working.|
|isOnline|String   |Online status, 1 for online, 0 for offline.|
|iotType|String   |See the following table for device type, enumeration and fields.|


#### Equipment fault status:

|Field|Illustration|
|:-----  |:-----      |
|OK    |No error|
|ERROR    |Error status (with unprocessed error information)|


#### Machine Type:

|Field|Illustration|
|:-----  |:-----      |
|NSELF_HELP_1    |Self service car washer 1|
|NFULL_AUTO_1    |Rollover car washer 1|
|NFULL_AUTO_2 |Rollover car washer 2 (No parking gate)|
|NFULL_AUTO_3 |Rollover car washer 3|
|NTUNNEL_1    |Tunnel car washer 1|
|WATER_PURIFIER_1 |Water purifier 1|