#### Description:
- After setting up the callback address in the management background, we will push the message to the URL you set when the device state changed.
- The open platform will send a post request to the specified address, and the contentType is application / JSON.
- If the merchant's callback interface returns 200, the callback is considered successful.

##### Example of sending JSON by callback:

```json
{
	"callTime": 12345667890,
	"callbackType": "FINISH_WASH",
	"washerId": 123456,
	"iotId":123456,
	"orderId":"ORDER123456"
}
```

#### Parameter Description:

|Parameter name|Type|Illustration|
|:----    |:----- |-----   |
|callTime  |long |Callback send timestamp   |
|callbackType   |String | Callback type, enumeration, see the following table. |
|Other fields   | | Depending on the callback type, there will be different numbers of other fields. See the callback description for details. |



#### Callback type:

|Field| Illustration                                                                            |
|:-----  |:----------------------------------------------------------------------------------------|
|FINISH_WASH| Car wash complete                                                                       |
|MACHINE_UPDATE_INFO| Equipment information update                                                            |
|MACHINE_UPDATE_STATUS| Device online status update                                                             |
|MACHINE_ERROR| Equipment error notification                                                            |
|MACHINE_FA_CAR_CHANGE| Vehicles position changes of Rollover car washer 1 and Rollover car washer 3.           |
|MACHINE_RT2_CAR_CHANGE| Change of vehicles parking state of the Rollover car washer 2 without parking gate.     |
|MACHINE_TT1_CAR_INTO| Tunnel car washer 1 vehicle entry.                                                      |
|MACHINE_TT1_CAR_PUSH_OUT| Tunnel car washer 1,the vehicle was rolled out.                                         |
|WP1_WORK_FINISH| Water purifier 1,water purifier pumping completion notice.                              |
|WP1_WAIT_TIMEOUT| Water purifier 1,water purifier operation timeout.                                      |
|WP1_START_WATER| Water purifier 1,the water purifier starts to discharge water.                          |
|WP1_CARD_CONSUME_READY| Water purifier 1,Notice of ready water outlet after successful swipe of water purifier. |
|WP1_UPLOAD_TDS| Water purifier 1,report TDS of water purifier.                                          |
|ZY_RT_PARK_CHANGE| Vehicles position changes of New Rollover car washer.                                   |