#### Brief description：

- Check the status of the equipment and return the current operation of the equipment.


#### Request URL:

- https://SERVER_URL/api/open/v1/common/checkStatus

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |time stamp   |
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
  "iotStatus" : "READY"
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
|code |int   |Error ID, if the value is 0, there is no error.  |
|msg |String   |Error message, When the code is not 0, this field prompts the specific error reason.|
|iotStatus |String   |For the enumeration of device status, see the following table.|

#### Device status enum:

|Field|Illustration|
|:-----  |:-----      |
|READY    |Ready|
|NOT_READY    |Not ready|
|WASHING    |Washing|
|OFFLINE    |Offline|
|CMD_ERROR    |The instruction does not apply.|
|NOT_ANSWER    |No response from car washer.|
|LOCKING    |The machine is locked.|
|ERROR    |Error|