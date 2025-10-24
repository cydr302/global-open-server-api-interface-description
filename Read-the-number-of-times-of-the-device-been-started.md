#### Brief description:

- Get the startup times information recorded in the device.
- Note: At present, only the reading of several types of [Self service car washer 1] [Rollover car washer 1] [Rollover car washer 2] [Rollover car washer 3] [Tunnel car washer 1] is supported.


#### Request URL:

- https://SERVER_URL/api/open/v1/common/checkWorkTime

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|iotId |No  |Long | Machine ID  |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2SSbf0ih",
	"time": 1613693307796,
	"iotId": 10044
}
```

**Response JSON:**

```
{
  "code" : 0,
  "workTime" : 12345
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
|workTime |Long |The number of starts. If - 1 is returned, it means that the read failed or the device type does not support reading.|
