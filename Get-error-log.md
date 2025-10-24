#### Brief description:

- Paging access to the history errors of a device.


#### Request URL:

- https://SERVER_URL/api/open/v1/common/pageError

#### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |time stamp   |
|iotId |Yes  |long | Machine ID    |
|page |No  |int | Page number    |
|size |No  |int | Number of per page (max. 20)    |

#### Request example:

**Request JSON:**

```
{
	"openId": "rSZWWixs2SSbf0ih",
	"time": 1613693307796,
	"page": 1,
	"size": 5,
	"iotId": 10024
}
```

**Response JSON:**

```
{
  "code" : 0,
  "resList" : [ {
    "errorMessage" : "[M835]Abnormal photoelectric signal of balance before and after top blowing(X035)",
    "createTime" : "2018-12-21 08:07:55",
    "hasDealt" : 0
  }, {
    "errorMessage" : "[M820]Photoelectric abnormality of container truck(X016)",
    "createTime" : "2018-12-21 08:07:55",
    "hasDealt" : 0
  }, {
    "errorMessage" : "[M819]Photoelectric abnormality of vehicle head(X015)",
    "createTime" : "2018-12-21 08:07:55",
    "hasDealt" : 0
  }, {
    "errorMessage" : "[M818]Photoelectric anomaly after top blowing(X014)",
    "createTime" : "2018-12-21 08:07:55",
    "hasDealt" : 0
  }, {
    "errorMessage" : "[M817]Photoelectric anomaly before top blowing(X013)",
    "createTime" : "2018-12-21 08:07:55",
    "hasDealt" : 0
  } ],
  "total" : 210
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
|resList |Array   |Data array for current page|
|errorMessage |String   |Error message text|
|createTime |String   |Error recording time|
|hasDealt |int   |Whether processed,1 yes,0 no|
|total |long   |Total data|