- This callback will be triggered when the locked device user presses the water outlet button and starts to water out. This callback will also be triggered when the user presses the water outlet button again after pausing. The actual water output shall be subject to the value in the callback at the end of pumping.

## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long|Machine ID   |
|orderId|String |Order ID  |