### Brief description:

- For the car washing order created before, the order flow can be obtained through this interface.


### Request URL:

- https://SERVER_URL/api/open/v1/advOrder/checkAdvOrder

### Request parameters:

|Parameter name|Required|Type|Illustration|
|:----    |:---|:----- |-----   |
|openId |Yes  |String |OpenID   |
|time|Yes  |long |Time stamp   |
|orderId |Yes  |String | Previously created order ID    |

### Request example:

**Request JSON:**

```
{
    "openId": "rSZWWixs2SSbf0ih",
    "time": 1613693307796,
    "orderId": "OC155157975002071"
}
```

**Response JSON:**

```
{
  "code" : 0,
  "advOrderList" : [ {
    "createTime" : "2018-04-18 17:59:17",
    "iotId" : 10044,
    "programId" : 33,
    "iotStatus" : "READY",
    "logType" : "RT_LOCK"
  },  {
    "createTime" : "2018-04-18 17:59:33",
    "iotId" : 10044,
    "iotStatus" : "READY",
    "logType" : "RT_CONF"
  }]
}
```

**Error example:**

```
{
  "code" : 20005,
  "msg" : "Parameter cannot be empty"
}
```

#### Return Parameter Description:

|Parameter name|Type|Illustration|
|:-----  |:-----|-----                           |
|code |int   |Error ID, a value of 0 indicates no error.  |
|msg |String   |Error message. When the code is not 0, this field prompts the specific error reason.|
|advOrderList |Array   |Equipment order flow information array.|
|createTime |String   |Event recording time.|
|iotId |long   |Machine ID|
|mark|int|Scheme mark|
|volume|int|Water quantity|
|iotStatus|String   |The return status of the device is enumerated in the table below.|
|logType|String   |Record type,enumeration, shown in the table below.|


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

#### Record type enumeration:

|Field|Illustration|
|:-----  |:-----      |
|RT_LOCK|Rollover car washer 1 lock|
|RT_CONF|Rollover car washer 1 start|
|RT_LOCK_CONF|Rollover car washer 1 lock and start|
|RT_STOP|Rollover car washer 1 emergency stop|
|RT2_CHECK_PARK|Rollover car washer 2 check parking|
|RT2_START|Rollover car washer 2 start|
|RT2_PAUSE|Rollover car washer 2 suspend|
|RT2_CONTINUE|Rollover car washer 2 continue|
|RT2_STOP|Rollover car washer 2 emergency stop|
|SH_START|Self service car washer 1 lock and start|
|NTT_START|New tunnel machine start washing|
|NTT_RESET|New tunnel machine reset|
|NTT_PAUSE|New tunnel machine suspend|
|NTT_CONTINUE|New tunnel machine continue|
|RT3_LOCK|Rollover car washer 3 lock|
|RT3_CONF|Rollover car washer 3 start|
|RT3_LOCK_CONF|Rollover car washer 3 lock and start|
|RT3_STOP|Rollover car washer 3 emergency stop|
|WP1_LOCK|Water purifier 1 lock|
|WP1_START|Water purifier 1 coming out of the water|
|WP1_CANCEL_LOCK|Water purifier 1 unlock|
|WP1_OPEN_DOOR|Water purifier 1 open the door|
|WP1_WOK_FNS|Water purifier 1 send out water|
|COM_WOK_FNS|Universal,car wash complete|
