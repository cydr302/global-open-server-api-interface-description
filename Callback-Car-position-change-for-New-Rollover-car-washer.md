## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long   |Machine ID|
|status |String   |Vehicle status, enumeration, see the table below.|


#### Status of vehicle in car washer:

| Field |Illustration|
|:------|:-----      |
| 0     |The parking position is correct.|
| 16    |The vehicle needs to move forward.|
| 17    |The vehicle needs to move back.||