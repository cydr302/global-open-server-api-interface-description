- This callback is triggered when the device reports water quality.

## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long|Machine ID   |
|sourceTds|int|Source water TDS  |
|cleanTds|int|Purified water TDS|