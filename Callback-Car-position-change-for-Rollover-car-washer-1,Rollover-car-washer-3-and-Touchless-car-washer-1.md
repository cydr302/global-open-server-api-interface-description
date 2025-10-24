## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long   |Machine ID|
|status |String   |Vehicle status, enumeration, see the table below.|


#### Status of vehicle in car washer:

|Field|Illustration|
|:-----  |:-----      |
|SUCCESS|The parking position is correct.|
|FAIL|Parking position error for unknown reason.|
|BACK|The vehicle needs to move back.|
|ENTER|The vehicle needs to move forward.|
|WAIT|Equipment idle, waiting for vehicle.|