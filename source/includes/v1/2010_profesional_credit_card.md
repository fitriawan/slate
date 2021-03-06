## Profesional Credit Card

### Profesional Credit Card Flow

![NICEPay API v1 Profesional Credit Card Flow](/images/v1/pro/flow/2010_profesional_credit_card_flow.png "NICEPay API v1 Profesional Credit Card Flow")

&nbsp;

### Profesional Credit Card Registration

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/orderRegist.do`
**Method** | POST
**Description** | Perform for Profesional Credit Card Registration
**Merchant Token** | `SHA256(iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Request Parameters for Profesional Credit Card Registration

```
    "iMid": "IONPAYTEST"
    "currency": "IDR"
    "amt": "10000"
    "instmntMon": "1"
    "referenceNo": "OrdNo-20190101010101"
    "goodsNm": "NICEPay Profesional"
    "payMethod": "01"
    "billingNm": "John Doe"
    "billingPhone": "08123456789"
    "billingEmail": "customer@merchant.com"
    "billingAddr": "Jl. Casablanca Raya Kav 88"
    "billingCity": "Jakarta"
    "billingState": "Jakarta Selatan"
    "billingPostCd": "12345"
    "billingCountry": "Indonesia"
    "deliveryNm": "Jane Doe"
    "deliveryPhone": "08123456789"
    "deliveryAddr": "Jl. Casablanca Raya Kav 88"
    "deliveryCity": "Jakarta"
    "deliveryState": "Jakarta Selatan"
    "deliveryPostCd": "12345"
    "deliveryCountry": "Indonesia"
    "callBackUrl": "https://merchant.com/callBackUrl"
    "dbProcessUrl": "https://merchant.com/notification"
    "vat": "0"
    "fee": "0"
    "notaxAmt": "0"
    "description": "NICEPay Profesional Credit Card Registration"
    "merchantToken": ""
    "reqDt": "20190101"
    "reqTm": "010101"
    "reqDomain": "https://merchant.com/"
    "reqServerIP": "127.0.0.1"
    "reqClientVer": "1.0"
    "userIP": "127.0.0.1"
    "userSessionID": ""
    "userAgent": "Mozilla"
    "userLanguage": "en-US"
    "instmntType": "2"
    "worker": "John Doe"
    "cartData": "{}"
    "paymentExpDt": "20190101"
    "paymentExpTm": "010101"
    "recurrOpt": "2"
    "timeStamp": "20190101010101"
    "version": "1.0"
```

> Sample Cart Data Parameter for Profesional Credit Card Registration (JSON)

```json
{
    "count": "2",
    "item": [
        {
            "img_url": "http://img.aaa.com/ima1.jpg",
            "goods_name": "Item 1 Name",
            "goods_detail": "Item 1 Detail",
            "goods_amt": "700"
        },
        {
            "img_url": "http://img.aaa.com/ima2.jpg",
            "goods_name": "Item 2 Name",
            "goods_detail": "Item 2 Detail",
            "goods_amt": "300"
        }
    ]
}
```

> Setting Cart Data Parameter for Profesional Credit Card Registration (JSON)

```json
    "cartData": "{\"count\": \"2\",\"item\": [{\"img_url\": \"http://img.aaa.com/ima1.jpg\",\"goods_name\": \"Item 1 Name\",\"goods_detail\": \"Item 1 Detail\",\"goods_amt\": \"700\"},{\"img_url\": \"http://img.aaa.com/ima2.jpg\",\"goods_name\": \"Item 2 Name\",\"goods_detail\": \"Item 2 Detail\",\"goods_amt\": \"300\"}]}"
```

**Request Parameters for Profesional Credit Card Registration**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
iMid | &#8730; | AN | 10 | Merchant ID 
currency | &#8730; | N | 3 | Currency 
amt | &#8730; | N | 12 | Goods Amount 
instmntMon | &#8730; | N | 2 | Installment Month 
referenceNo | &#8730; | ANS | 40 | Merchant Order No 
goodsNm | &#8730; | AN | 100 | Goods Name 
payMethod | &#8730; | AN | 2 | Payment Metohd, <br/> refer code at [Here](#payment-method) 
billingNm | &#8730; | A | 30 | Buyer Name 
billingPhone | &#8730; | N | 15 | Buyer Phone Number 
billingEmail | &#8730; | AN | 40 | Buyer Email 
billingAddr | &nbsp; | AN | 100 | Buyer Address 
billingCity | &#8730; | A | 50 | Buyer City 
billingState | &#8730; | A | 50 | Billing State 
billingPostCd | &#8730; | N | 10 | Billing Post Number 
billingCountry | &#8730; | A | 10 | Billing Country 
deliveryNm | &nbsp; | A | 30 | Delivery Name 
deliveryPhone | &nbsp; | N | 15 | Delivery Phone Number 
deliveryAddr | &nbsp; | AN | 100 | Delivery Address 
deliveryCity | &nbsp; | A | 50 | Delivery City 
deliveryState | &nbsp; | A | 50 | Delivery State 
deliveryPostCd | &nbsp; | N | 10 | Delivery Post Number 
deliveryCountry | &nbsp; | A | 10 | Delivery Country 
callBackUrl | &#8730; | AN | 255 | Payment Result Forward Url <br/> (on browser) 
dbProcessUrl | &#8730; | AN | 255 | Payment Notification Url <br/> (server side) 
vat | &nbsp; | N | 12 | Vat 
fee | &nbsp; | N | 12 | Service Fee 
notaxAmt | &nbsp;| N | 12 | Tax Free Amount 
description | &nbsp; | AN | 100 | Transaction Description 
merchantToken | &#8730; | AN | 255 | Merchant Token 
reqDt | &nbsp; | N | 8 | Request Date <br/> (YYYYMMDD) 
reqTm | &nbsp; | N | 6 | Request Time <br/> (HH24MISS) 
reqDomain | &nbsp; | AN | 100 | Request Domain 
reqServerIP | &nbsp; | AN | 15 | Request Server IP 
reqClientVer | &nbsp; | AN | 50 | Request Client Version 
userIP | &#8730; | AN | 15 | User IP <br/> (customer) 
userSessionID | &nbsp; | AN | 100 | User Session ID 
userAgent | &nbsp; | AN | 100 | User Agent Information 
userLanguage | &nbsp; | A | 2 | User Language 
instmntType | &#8730; | N | 2 | Installment Type, <br/> refer code at [Here](#installment-type) 
worker | &nbsp; | AN | 10 | Worker 
cartData | &#8730; | AN | 4000 | Cart Data 
paymentExpDt | &nbsp; | N | 8 | Permit Time Check Date <br/> (YYYYMMDD) 
paymentExpTm | &nbsp; | N | 6 | Permit Time Check Time <br/> (HH24MISS) 
recurrOpt | &#8730; | N | 2 | Recurring Option, <br/> *Only for Credit Card `Recurring`*, <br/> refer code at [Here](#recurring-option) 
timeStamp | &nbsp; | N | &nbsp; | Timestamp 
version | &nbsp; | AN | &nbsp; | Version 

&nbsp;

**Cart Data Parameter for Profesional Credit Card Registration**

Parameter | Description 
---------- | ---------- 
count | Total card data count 
item | &nbsp; 
Item -> img_url | good's image URL <br/> (image size 50*50) 
Item -> goods_name | goods name 
Item -> goods_detail | goods detail description 
Item -> goods_amt | goods transaction amount

&nbsp; 

> Sample Response Parameters for Profesional Credit Card Registration (JSON)

```json
{
    "apiType": "M0",
    "tXid": "",
    "requestDate": "",
    "responseDate": "",
    "data": {
        "tXid": "",
        "resultCd": "0000",
        "resultMsg": "SUCCESS",
        "requestURL": "https://www.nicepay.co.id/nicepay/api/orderInquiry.do"
    }
}
```

**Response Parameters for Profesional Credit Card Registration**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ---------- 
apiType | &nbsp; | 2 | Api Type | &nbsp; 
tXid | AN | 30 | Transaction ID | &nbsp; 
requestDate | &nbsp; | &nbsp; | Request Date | &nbsp; 
responseDate | &nbsp; | &nbsp; | Response Date | &nbsp; 
data | Array of Object | &nbsp; | Api Data | &nbsp; 

&nbsp;

**Response Parameters `data` for Profesional Credit Card Registration**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ---------- 
tXid | AN | 30 | Transaction ID | &nbsp; 
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
requestURL | &nbsp; | 255 | Reqeust URL | &nbsp; 

&nbsp;

### Profesional Credit Card Payment

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/orderInquiry.do`
**Method** | URL POST
**Description** | Perform for Profesional Credit Card Payment

&nbsp;

> Sample Request Parameters for Profesional Credit Card Payment (URL POST)

```
https://www.nicepay.co.id/nicepay/api/orderInquiry.do?tXid={tXid}&optDisplayCB=0&optDisplayBL=0
```

**Request Parameters for Profesional Credit Card Payment**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
tXid | &#8730; | AN | 30 | Transaction ID <br/> (Key from NICEPay) 
optDisplayCB | &nbsp; | N | 2 | Option Display Change Button 
optDisplayBL | &nbsp; | N | 2 | Option Display Back To The Link 

&nbsp;

![NICEPay API v1 Profesional Credit Card Payment](/images/v1/pro/pay/2010_profesional_credit_card_payment.jpg "NICEPay API v1 Profesional Credit Card Payment")

&nbsp;

> Sample Response Parameters for Profesional Credit Card Payment

```
https://example.com/callBackUrl?resultCd={resultCd}&resultMsg={resultMsg}&authNo={authNo}&tXid={tXid}&referenceNo={referenceNo}&transDt{transDt}&transTm={transTm}&amount={amount}&recurringToken={recurringToken}&preauthToken={preauthToken}&description={description}&cardNo={cardNo}&acquBankCd={acquBankCd}&issuBankCd={issuBankCd}&vat={vat}&fee={fee}&notaxAmt={notaxAmt}
```

**Response Parameters for Profesional Credit Card Registration**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ---------- 
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
authNo | N | 10 | Authorization Number | &nbsp; 
tXid | AN | 30 | Transaction ID <br/> (Key from NICEPay) | &nbsp; 
referenceNo | ANS | 40 | Merchant Order No | &nbsp; 
transDt | N | 8 | Transaction Date <br/> (YYYYMMDD) | &nbsp; 
transTm | N | 6 | Transaction Time <br/> (HH24MISS) | &nbsp; 
amount | N | 12 | Transaction Amount | &nbsp; 
recurringToken | AN | 64 | Token That Using Recurring payment | &nbsp; 
preauthToken | AN | 64 | Token That Using Capture process | &nbsp; 
description | AN | 100 | Transaction Description | &nbsp; 
cardNo | AN | 20 | Card Number | &nbsp; 
acquBankCd | A | 4 | Acquire Bank Code, <br/> refer code at [Here](#bank-code) | &nbsp; 
issuBankCd | A | 4 | Issue Bank Code, <br/> refer code at [Here](#bank-code) | &nbsp; 
vat | N | 12 | Vat | &nbsp; 
fee | N | 12 | Service Fee | &nbsp; 
notaxAmt | N | 12 | Tax Free Amount | &nbsp; 