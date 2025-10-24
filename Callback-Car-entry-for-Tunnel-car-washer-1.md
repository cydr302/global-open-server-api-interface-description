## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long   |Machine ID|
|status |String   |Vehicle entry status,enumeration,see the table below.|


#### Car entry status:

|Field|Illustration|
|:-----  |:-----      |
|SUCCESS|The parking position is correct.|
|INTO_TIME_OUT|Vehicle entry timeout.|