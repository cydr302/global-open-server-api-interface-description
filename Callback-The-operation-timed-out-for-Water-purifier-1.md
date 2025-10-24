- The timeout of no operation after locking and the timeout of pause after water exit will trigger this callback. After sending this callback, the callback of water exit will be sent.

## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long|Machine ID   |
|orderId|String |Order ID  |