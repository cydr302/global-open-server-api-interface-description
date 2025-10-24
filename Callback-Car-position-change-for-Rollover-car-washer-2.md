## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long   |Machine ID|
|status |String   |Vehicle parking status, enumeration, see the table below.|


#### Vehicle parking status:

|Field|Illustration|
|:-----  |:-----      |
|SUCCESS|The parking position is correct.|
|BACK|The vehicle needs to move back.|
|FORWARD|The vehicle needs to move forward.|
|WAIT|Equipment idle, waiting for vehicle.|