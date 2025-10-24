### When the user initiates an active car washing request, the server will send the following request to the URL you specified：

|item|value|
|:----    |:----- |
|Request method|POST|
|ContentType|application/json|
|Connection timed out|2000ms|
|Read timeout|20000ms|

### Business introduction
- Swipe the car

When the user swipes the card in the Self service car washer, the merchant can control whether the card can start the device, and can specify the car washing scheme ID that the card can use.
Use the isok field to control whether to start the machine.
Use the balance field to control the balance information displayed by the device to the user.
The server will check whether the scheme ID is available in the device when it receives your return isok of 1. If available, the scheme will be used to start the car washer directly.

- License plate recognition

After the user's vehicle triggers the license plate recognition camera, you can control whether to open the gate.
Use the isok field to control whether the parking gate is lifted.
Use the balance field to control the balance information displayed by the device to the user.

When the server receives the isok of 1, it lifts the parking gate to release. At this time, the car washing machine is not locked. You need to control the locking and starting of the equipment.


- Water purifier 1 swipe card

When the user swipes the card, the merchant can control whether the card can start the device, and specify the water output, waiting time-out and other information.
Use the isok field to control whether to send water to the machine and lock the device.
Use the balance field to control the balance information displayed by the device to the user.
When the server receives the isok of 1, it will send water and lock the machine. At this time, the device is in the locked state, which is the same as the follow-up process of actively calling the interface of the distribution scheme. The user also needs to press the water button on site.

### Request parameters:

**Request example:**

```
{
	"callTime": 12345667890,
	"iotId": 123456,
        "callType": "CARD_WASH",
	"cardNum": "ABCD1234567",
}
```

```
{
	"callTime": 12345667890,
	"iotId": 123456,
        "callType": "CAR_PLATE",
	"carPlateNum": "Beijing A123456"
}
```

#### Request parameter description:

|Parameter name|Type|Illustration|
|:-----  |:-----|-----                           |
|callTime|long |The time stamp for sending the callback.  |
|iotId|long |Machine ID|
|callType|String |Request type，enumeration，shown in the table below.|
|cardNum|String |Card number,When calltype is card_ Wash is valid.|
|carPlateNum|String |license plate,When calltype is car_plate is valid.|


#### Request type enumeration:

|Field|Illustration|
|:-----  |:-----  |
|CARD_WASH|Swipe the car|
|CAR_PLATE|License plate recognition|
|WP1_SWIPE_CARD|Water purifier 1 swipe card|


#### After you receive the request, you should process the withholding fee and check the availability of license plate or card according to your business logic. After processing the business logic, return to HTTP status code=200 and reply to the following Json with the same parameters:

```
{
	"isOk": 1,
	"mark": 1,
        "balance": 10000,
}
```

#### response parameter description:
|Parameter name|Type|Required|Illustration|
|:-----  |:-----|:-----|-----      |
|isOk|int |Yes|Is this car wash request allowed? 1 Yes 0 No|
|mark|int |Yes|Scheme mark,Currently support 1,2,3.|
|balance |long |Yes|The balance shown to the user on the device.|
|orderId |String |Yes|Order ID generated for this swipe.|
|volume|int|No |Water yield(ml),It should be a multiple of 100,When calltype is Wp1_SWIPE_Card is required.|
|maxWaitTime|int|No |Maximum waiting timeout(second),Range 30-120 ,When calltype is Wp1_SWIPE_Card is required.|