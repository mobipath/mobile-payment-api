# USSD-Payment-API

All required api with documentation

## Payment Getway API Documentation

### Payment API Request Link

Create: <https://api.mobipath.online/api/v1/payment/ussd/beta/create>

Execute: <https://api.mobipath.online/api/v1/payment/ussd/beta/execute>

Request Method: POST

# API Create Request

## Create Request: 

Create: <https://api.mobipath.online/api/v1/payment/ussd/beta/create>

```json
    {
        "username": "xxxx",
        "password": "xxxx",
        "studentId": "xx.xxxx"
    }
```

Here username and password are given by mobipath. The Student ID must contain the institute ID.

## Create Response: 

API response the condition based on status. The Success response status is 200. 
The Default status. Other error and information status code will be listed under the json.

```json
    {
        "message": "User Details With Payment Info",
        "name": "XX XX XX",
        "amount": 100,
        "transactionId": "TRX15587732467279182",
        "timestamp": "2019-05-25T08:34:06.740Z"
    }
```

[Note]: This way the transaction was created. But its only valid for 2 hour. After the that time the create transaction need to new request. Every Request the transaction ID was unique. A single user can request a transaction ones. If in the transaction any new request get then the old request will be invalid.

#### The Error Code and there messages

##### Status Code 250 = All Request Property Not Found

##### Status Code 265 = No Invoice Found

##### Status Code 261 = Student Information Not Found

##### Status Code 199 = Internal Error

##### Status Code 280 = Username or Password invalid

## Execute Request: 

Execute: <https://api.mobipath.online/api/v1/payment/ussd/beta/execute>

```json
{
	"studentId": "xx.xxxx",
	"amount": "xxx",
	"paymentId": "xxxx",
	"paymentTo": "xxxxxxxxxx",
	"paymentFrom": "xxxxxx",
	"transactionId": "TRXxxxxxxxx",
	"timestamp" : "2018-04-19T12:22:46.236Z"
}
```

[Note]: The payment ID shoud be send from ussd. Without payment ID the transaction will not success or Finish.

## Execute Response: 

Success status Return with code 200

```json
    {
        "transactionStatus": true,
        "message": "payment success"
    }
```

Payment Success.

#### The Error Code and there messages

##### Status Code 250 = All Request Property Not Found

##### Status Code 270 = Response Timeout

##### Status Code 271 = Transaction ID not Matched

##### Status Code 260 = No Invoice Found

##### Status Code 272 = Amount Not Match, Check Amount

##### Status Code 199 = System Error

##### Status Code 255 = Payment Not Success

## -----------------------------------------

## Any issue knock us

# ------ Thank You ------------