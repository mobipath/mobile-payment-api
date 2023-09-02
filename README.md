# Billpay USSD Payment API

All required api with documentation

## Payment Getway API Documentation

## Bkash Payment API Request Link

QueryBill: </api/v1/payment/ussd/bkash/queryBill>

PayBill: </api/v1/payment/ussd/bkash/payBill>

SearchTransaction: </api/v1/payment/ussd/bkash/searchTransaction>

# API Request & Response

## QueryBill Request:

QueryBill: </api/v1/payment/ussd/bkash/queryBill>

Method: POST

```json
    {
        "UserName": "XXXXXXX",
        "Password": "XXXXXXX",
        "StudentId": "XXXXXX",
        "BillMonth": "XXXXXX", // "022023"
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
        "ErrorCode": "XXX", // "200"
        "ErrorMsg": "XXXXXXXX", // "Success"
        "BillMonth": "XXXXXX", // "022023"
        "BillAmount": "XXXX", // "2360"
        "BillDueDate": "XXXXXXXX", // "20240226"
        "QueryTime": "XXXXXXXXXXXXXX", // "20230830061008"
        "AmountBreakdown": {
            "TotalServiceCharge": 20,
            "TotalInvoice": 2
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

PayBill: </api/v1/payment/ussd/bkash/payBill>

Method: POST

```json
    {
        "UserName": "XXXXXXX",
        "Password": "XXXXXXX",
        "StudentId": "XXXXXX",
        "BillMonth": "XXXXXX", // "022023"
        "merchantWalletNo": "XXXXXXXXXXX",
        "Amount": "XXXX", // "2360"
        "UserMobileNumber": "01521XXXXXX", // "Not Mandatory"
        "TrxId": "XXXXXXXXXX",
        "PayTime": "XXXXXXXXXXXX", // "20230828193516"
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
        "ErrorCode": "XXX", // "200"
        "ErrorMsg": "XXXXXXXX", // "Success"
        "ConsumerName": "XXX XXX XXX",
        "TotalAmount": "XXXX", // "2360"
        "TrxId": "XXXXXXXXXX",
        "MiddlewarePayTime": "XXXXXXXXXXXXX", // "20230830064416"
        "RefNumber": "01777515669",
        "AmountBreakdown": {
            "TotalServiceCharge": 20,
            "TotalInvoice": 2
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

SearchTransaction: </api/v1/payment/ussd/bkash/searchTransaction>

Method: POST

```json
    {
        "UserName": "XXXXXXX",
        "Password": "XXXXXXX",
        "TrxId": "XXXXXXXXXX"
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
        "ErrorCode": "XXX", // "200"
        "ErrorMsg": "XXXXXXXX", // "Success"
        "TotalAmount": XXXX, // "2360"
        "TrxId": "XXXXXXXXXX",
        "MiddlewarePayTime": "XXXXXXXXXXXXX", // "20230830064416"
        "RefNumber": "01777515669",
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
