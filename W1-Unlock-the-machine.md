#### Brief description:

- It is recommended to check whether the equipment status is locked or working before calling this interface.
- After receiving this command, the locked device will unlock and wait for new work. The working device will end its work and send a completion callback normally.
- The unlocked order number should be consistent with the order number of the source of the lock operation.


#### Request URL:

- https://SERVER_URL/api/open/v1/wp1/cancelLock

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |Yes  |long | Machine ID    |
|orderId |Yes  |String | The order number in your system should be consistent with that of the lock operation.    |

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
|OFFLINE    |Offline|
|WP_MAKING    |Water making|
|CMD_ERROR    |The instruction does not apply.|
|NOT_ANSWER    |No response from water purifier.|
|WP_LOCKING |Water purifier is locked.|
|WP_RUNNING |Water purifier is working.|
|WP_DISABLE |Water purifier is disabled.|
|WP_PAUSING |Pause the water purifier.|
|ERROR    |Error|