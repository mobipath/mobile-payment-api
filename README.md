# Mobipath - Rocket PayBill(USSD) Payment Webhook

All required api with documentation

## Payment Getway API Documentation

## Rocket Payment API Request Link

QueryBill: </api/v1/payment/ussd/rocket/paymentValidation>

PayBill: </api/v1/payment/ussd/rocket/paymentConfirmation>

SearchTransaction: </api/v1/payment/ussd/rocket/getPaymentStatus>

# API Request & Response

## QueryBill Request:

QueryBill: </api/v1/payment/ussd/rocket/paymentValidation>

Method: POST

```json
    {
        "userId"        : "XXXXXXX",
        "password"      : "XXXXXXX",
        "studentId"     : "XXXXXX",
        "merchantWalletNo": "XXXXXXXXXXX"
    }
```

```
    Here Username and Password are given by mobipath.
```

## QueryBill Response: 

API response the condition based on status. The Success response status is 200. 
The Default status. Other error and information status code will be listed under the json.

```json
    {
        "errorCode"     : "XXX", // "200"
        "errorMsg"      : "XXXXXXXX", // "Success"
        "studentName"   : "xxxxxxxx",
        "billAmount"    : "XXXX", // "2360"
        "billDueDate"   : "XXXXXXXX", // "20240226"
        "queryTime"     : "XXXXXXXXXXXXXX", // "20230830061008"
        "amountBreakdown": {
            "totalServiceCharge": 20,
            "totalInvoice": 2
        }
    }
```

[Note]: This way the transaction was created. But its only valid for 6 months. After the that time the create transaction need to new request. Every Request the transaction ID was unique. A single user can request a transaction ones. If in the transaction any new request get then the old request will be invalid.

#### The ErrorCode and their ErrorMsg

##### Status Code 200 = Success

##### Status Code 403 = Authentication Failed

##### Status Code 404 = Data Not Found

##### Status Code 406 = Mandatory Field missing

##### Status Code 435 = Data Mismatch

##### Status Code 436 = Already Paid

<!-- ##### Status Code 437 = Due date over

##### Status Code 438 = Minimum amount not paid

##### Status Code 439 = Pay amount and biller amount not match -->

##### Status Code 440 = Unknown Error, try again.

## PayBill Request:

PayBill: </api/v1/payment/ussd/rocket/paymentConfirmation>

Method: POST

```json
    {
        "userId"        : "XXXXXXX",
        "password"      : "XXXXXXX",
        "studentId"     : "XXXXXX",
        "merchantWalletNo": "XXXXXXXXXXX",
        "amount"        : "XXXX", // "2360"
        "trxId"         : "XXXXXXXXXX",
        "trxDate"       : "XXXXXXXXXXXX", // "20230828193516"
    }
```

```
    Here Username and Password are given by mobipath.
```

## PayBill Response: 

API response the condition based on status. The Success response status is 200. 
The Default status. Other error and information status code will be listed under the json.

```json
    {
        "errorCode"         : "XXX", // "200"
        "errorMsg"          : "XXXXXXXX", // "Success"
        "studentName"       : "XXX XXX XXX",
        "totalAmount"       : "XXXX", // "2360"
        "trxId"             : "XXXXXXXXXX",
        "middlewarePayTime" : "XXXXXXXXXXXXX", // "20230830064416"
        "refNumber"         : "017XXXXXXXX",
        "amountBreakdown"   : 
        {
            "totalServiceCharge": 20,
            "totalInvoice"      : 2
        }
    }
```

[Note]: The Transaction ID(TrxId) should be send from ussd. Without Transaction ID the transaction will not success or Finish.

#### The ErrorCode and their ErrorMsg

##### Status Code 200 = Success

##### Status Code 403 = Authentication Failed

##### Status Code 404 = Data Not Found

##### Status Code 406 = Mandatory Field missing

##### Status Code 435 = Data Mismatch

##### Status Code 436 = Already Paid

<!-- ##### Status Code 437 = Due date over

##### Status Code 438 = Minimum amount not paid

##### Status Code 439 = Pay amount and biller amount not match -->

##### Status Code 440 = Unknown Error, try again.

## SearchTransaction Request:

SearchTransaction: </api/v1/payment/ussd/rocket/getPaymentStatus>

Method: POST

```json
    {
        "userId": "XXXXXXX",
        "password": "XXXXXXX",
        "trxId": "XXXXXXXXXX"
    }
```

```
    Here Username and Password are given by mobipath.
```

## SearchTransaction Response: 

API response the condition based on status. The Success response status is 200. 
The Default status. Other error and information status code will be listed under the json.

```json
    {
        "errorCode": "XXX", // "200"
        "errorMsg": "XXXXXXXX", // "Success"
        "totalAmount": XXXX, // "2360"
        "trxId": "XXXXXXXXXX",
        "middlewarePayTime": "XXXXXXXXXXXXX", // "20230830064416"
        "refNumber": "017XXXXXXXX",
    }
```

[Note]: The Transaction ID(TrxId) should be send from ussd. Without Transaction ID the transaction will not success or Finish.

#### The ErrorCode and their ErrorMsg

##### Status Code 200 = Success

##### Status Code 403 = Authentication Failed

##### Status Code 404 = Data Not Found

##### Status Code 406 = Mandatory Field missing

<!-- ##### Status Code 435 = Data Mismatch

##### Status Code 436 = Already Paid

##### Status Code 437 = Due date over

##### Status Code 438 = Minimum amount not paid

##### Status Code 439 = Pay amount and biller amount not match -->

##### Status Code 440 = Unknown Error, try again.


## -----------------------------------------

## Any issue knock us with info@mobipath.com

# ------ Thank You ------------
