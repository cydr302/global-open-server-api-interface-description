- The user swipes the card and requests the merchant server through the active operation interface. After returning to the isok, the device is ready to trigger this callback.
- This callback indicates that the device is locked successfully, and the user can press the water button to continue the operation.

## Request parameters:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime   |long |The time stamp for sending the callback.   |
|callbackType   |String |Callback type   |
|iotId |long|Machine ID   |
|orderId|String |Order ID  |