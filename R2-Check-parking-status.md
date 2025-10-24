#### Brief description:

- Check the parking condition of the vehicle.


#### Request URL:

- https://SERVER_URL/api/open/v1/rt2/checkParkStatus

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |Yes  |long | Machine ID    |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2CUbf0ih",
	"time": 1613693307796,
	"iotId": 10024
}
```

**Response JSON:**

```
{
  "code" : 0,
  "rt2ParkStatus" : "SUCCESS"
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
|code |int   |Error ID, a value of 0 indicates no error.  |
|msg |String   |Error message. When the code is not 0, this field prompts the specific error reason.|
|rt2ParkStatus|String   |Parking status enumeration, see the following table for specific status.|

#### Device status enumeration:

|Field|Illustration|
|:-----  |:-----      |
|SUCCESS    |Parking ready|
|BACK    |need to step back|
|FORWARD    |need to move forward|
|WAIT    |Waiting for vehicles|