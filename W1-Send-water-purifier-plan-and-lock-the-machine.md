#### Brief description:

- It is recommended to check whether the device status is ready before calling this interface.
- If the interface is called successfully, the device is locked and waiting for the user to operate. At this time, the order cannot be placed repeatedly.



#### Request URL:

- https://SERVER_URL/api/open/v1/wp1/lock

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |Yes  |long | Machine ID    |
|volume|Yes  |int | Water output (ml)    |
|orderId |Yes  |String | The order number in your system is unique.    |
|maxWaitTime |Yes |int |Maximum waiting timeout(second),range 30-120.    |
|programPrice|Yes  |long | Price    |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2CUbf0ih",
	"time": 1613693307796,
	"iotId": 10024,
	"volume": 2000,
	"orderId": "ORDER12345",
        "maxWaitTime": 60,
        "programPrice":100
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
|iotStatus |String   |If the lock is successful,ready is returned. If other status is returned, indicating that the device is not ready or the lock fails, see the following table for specific status.|


#### Device status enumeration:

|Field|Illustration|
|:-----  |:-----      |
|READY    |Ready|
|NOT_READY    |Not ready|
|OFFLINE    |Offline|
|CMD_ERROR    |The instruction does not apply.|
|NOT_ANSWER    |No response from water purifier.|
|WP_MAKING    |Water making|
|WP_LOCKING |Water purifier is locked.|
|WP_RUNNING |Water purifier is working.|
|WP_DISABLE |Water purifier is disabled.|
|WP_PAUSING |Pause the water purifier.|
|ERROR    |Error|