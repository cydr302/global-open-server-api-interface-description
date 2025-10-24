## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long   |Machine ID|
|name |String   |Machine name|
|country|String   |country|
|address |String   |Machine address|
|longitude|double   |Longitude of location|
|latitude|double   |Latitude of location|
|errorStatus |String   |Error status,enumeration,the fields are shown in the table below.If the device has reported an error and has not handled it, the device is in the error state.A device with an error status does not mean that the device is not working.|
|onlineStatus |String   |Online status,enumeration,the fields are shown in the table below.|
|machineType |String   |Machine type,enumeration,the fields are shown in the table below.|




#### Equipment error status:

|Field|Illustration|
|:-----  |:-----      |
|OK    |No fault|
|ERROR    |Fault status (with unprocessed fault information)|


#### Device online status:

|Field|Illustration|
|:-----  |:-----      |
|ONLINE    |Online|
|OFFLINE    |Offline|


#### Equipment type:

|Field|Illustration|
|:-----  |:-----      |
|NSELF_HELP_1    |Self service car washer 1|
|NFULL_AUTO_1    |Rollover car washer 1|
|NFULL_AUTO_2    |Rollover car washer 2|
|NFULL_AUTO_3    |Rollover car washer 3|
|NTUNNEL_1    |Tunnel car washer 1|
|WATER_PURIFIER    |Water purifier 1|