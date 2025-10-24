#### Brief description:

- The car wash continues to operate.



#### Request URL:

- https://SERVER_URL/api/open/v1/rt2/continue

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
|iotStatus |String   |If the operation is successful, return ready. If other status is returned, the device is not ready or the operation failed. The specific status is shown in the table below.|

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