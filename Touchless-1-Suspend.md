#### Brief description:

- Suspension of car washing machine.



#### Request URL:

- https://SERVER_URL/api/open/v1/nt1/pause

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |Yes  |long | Machine ID    |
|orderId |Yes  |String | The order number in your system is unique.    |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2CUbf0ih",
	"time": 1613693307796,
	"iotId": 10024,
	"orderId": "ORDER12345"
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
|code |int   |Error ID, a value of 0 indicates no error.  |
|msg |String   |Error message. When the code is not 0, this field prompts the specific error reason.|
|iotStatus |String   |If the operation is successful,ready is returned. If other status is returned, indicating that the device is not ready or the lock fails, see the following table for specific status.|

#### Device status enumeration:

|Field|Illustration|
|:-----  |:-----      |
|READY    |Ready|
|NOT_READY    |Not ready|
|WASHING    |Washing|
|OFFLINE    |Offline|
|CMD_ERROR    |The instruction does not apply.|
|CAR_ERROR    |The car not stop well.|
|NOT_ANSWER    |No response from car washer.|
|LOCKING    |The machine is locked.|
|ERROR    |Error|