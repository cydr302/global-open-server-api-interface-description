#### Brief description:

- It is recommended to check whether the device status is ready before calling this interface.
- If the interface is called successfully, the device will work directly.
- It is recommended to use this interface to start the equipment without parking gate.
- It is not recommended to use this interface for equipment with parking gate.


#### Request URL:

- https://SERVER_URL/api/open/v1/nrt/lockAndStart

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |Yes  |long | Machine ID    |
|mark|Yes  |int| Scheme mark,currently support 1,2,3.    |
|orderId |Yes  |String | The order number in your system is unique.    |
|obstacleMark |No |String   |Vehicle obstacle marking:Three digit 0 or 1 identification string, 1 for obstacles, 0 for no obstacles.first, the roof rack. Second, front bumper. Third, the spare tire rack. For example, "100" stands for obstacles in the roof rack, "110" stands for obstacles in the bumper and roof, "000" stands for barrier free.    |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2CUbf0ih",
	"time": 1613693307796,
	"iotId": 10024,
	"mark": 2,
	"orderId": "ORDER12345",
    "obstacleMark": "000"
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
|iotStatus |String   |If the lock is successful, ready is returned. If other status is returned, indicating that the device is not ready or the lock fails, see the following table for specific status.|


#### Device status enumeration:

|Field| Illustration                |
|:-----  |:----------------------------|
|READY    | Ready                       |
|NOT_READY    | Not ready                   |
|WASHING    | Washing                     |
|OFFLINE    | Offline                     |
|NRT_CAR_NEED_FORWARD    | The car need forward        |
|NRT_CAR_NEED_BACK    | The car need back           |
|NRT_DISABLE    | The machine is disabled     |
|NRT_THAWING    | The machine is thawing      |
|NRT_UNLOCKED    | The machine is unlocked     |
|NOT_ANSWER    | No response from car washer |
|LOCKING    | The machine is locked       |
|ERROR    | Error                       |