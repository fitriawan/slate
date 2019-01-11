## Enterprise Credit Card

### Enterprise Credit Card Flow

![NICEPay API v1 Enterprise Credit Card Flow](/images/v1/ent/flow/3010_enterprise_credit_card_flow.jpg "NICEPay API v1 Enterprise Credit Card Flow")

&nbsp;

### Enterprise Credit Card Request Token

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/onePassToken.do`
**Method** | POST
**Description** | Perform for Enterprise Credit Card Request Token (One Time Use Transaction Token)
**Merchant Token** | `SHA256(iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Parameters for Enterprise Credit Card Request Token

```
api/onePassToken.do?jsonData={"cardNo":"","cardExpYymm":"","cardHolderNm":"","amt":"","referenceNo":"","merchantToken":"","iMid":"","instmntType":"","instmntMon":""} 
```

**Request Parameters for Enterprise Credit Card Request Token**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
cardNo | &#8730; | N | &nbsp; | Card Number 
cardExpYymm | &#8730; | N | 4 | Card Expiry <br/> (YYMM) 
cardHolderNm | &#8730; | AN | 50| Card Holder Name <br/> Only for Credit Card `CIMB` 
amt | &#8730; | N | 12 | Payment Amount 
referenceNo | &#8730; | ANS | 40 | Merchant Order Number 
merchantToken | &#8730; | AN | 255 | Merchant Token 
iMid | &#8730; | AN | 10 | Merchant ID 
instmntType | &#8730; | N | 2 | Installment Type, <br/> refer code at [Here](#installment-type) 
instmntMon | &#8730; | N | 2 | Installment Month 

&nbsp;

> Sample Response Parameter for Enterprise Credit Card Request Token 

```json
{
	"resultCd": "0000",
	"resultMsg": "SUCCESS",
	"cardToken": "",
	"paymentType": "1"
}
```

**Response Parameters for Enterprise Credit Card Request Token**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ---------- 
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
cardToken | AN | 64 | One Time Use Transaction Token | &nbsp; 
paymentType | N | 1 | Credit Card Authorization Type, <br/> refer code at [Here](#payment-type) | &nbsp; 

&nbsp;

### Enterprise Credit Card Payment 3D Secure

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/secureVeRequest.do`
**Method** | Perform for Enterprise Credit Card Payment 3D Secure (Popup Page)
**Description** | When you receive *`"paymentType":"1"`* on `onePassToken.do`, using this API Popup Page to input customer OTP

&nbsp;

> Sample Request Parameters for Enterprise Credit Card Payment 3D Secure (Popup Page)

```
https://www.nicepay.co.id/nicepay/api/secureVeRequest.do?country=360&callbackUrl={callbackUrl}&onePassToken={onePassToken} 
```

**Request Parameters for Enterprise Credit Card Payment 3D Secure (Popup Page)**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
country | &#8730; | N | 3 | Currency Code 
callbackUrl | &#8730; | AN | 200 | Result Callback Url 
onePassToken | &#8730; | AN | 64 | One Time Use Transaction Token 

&nbsp;

> Sample Response Parameter for Enterprise Credit Card Payment 3D Secure (Async Callback)

```
http://merchant.com/callbackUrl?resultCd=null&resultMsg=null 
```

**Response Parameter for Enterprise Credit Card Payment 3D Secure (Async Callback)**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ----------
resultCd | N | 4 | Result Code | When Success 
resultMsg | AN | 255 | Result Message | When Success 
referenceNo | ANS | 40 | Merchant Order Number | &nbsp; 
merchantToken | AN | 255 | Merchant Token | &nbsp; 

&nbsp;

### Enterprise Credit Card Payment MIGS

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/migsRequest.do`
**Method** | Perform for Enterprise Credit Card Payment MIGS (Popup Page)
**Description** | When you receive *`"paymentType":"3"`* on `onePassToken.do`, using this API Popup Page to input customer OTP (MIGS Authentication)

&nbsp;

> Sample Request Parameters for Enterprise Credit Card Payment MIGS (Popup Page)

```
https://www.nicepay.co.id/nicepay/api/migsRequest.do?instmntType=1&instmntMon=1&referenceNo={referenceNo}&cardCvv={cardCvv}&callbackUrl={callbackUrl}&onePassToken={onePassToken} 
```

**Request Parameters for Enterprise Credit Card Payment MIGS (Popup Page)**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
instmntType | &nbsp; | N | 2 | Installment Type, <br/> refer code at [Here](#installment-type)
instmntMon | &nbsp; | N | 2 | Installment Month 
referenceNo | &#8730; | ANS | 40 | Merchant Order Number 
cardCvv | &nbsp; | N | 3 | Card CVV 
callbackUrl | &#8730; | AN | 200 | Result Callback URL 
onePassToken | &#8730; | AN | 64 | One Time Use Transaction Token 

&nbsp;

> Sample Response Parameter for Enterprise Credit Card Payment MIGS (Async callback)

```
http://merchant.com/callbackUrl?resultCd=null&resultMsg=null 
```

**Response Parameter for Enterprise Credit Card Payment MIGS (Async callback)**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
resultCd | N | 4 | Result Code | When Success 
resultMsg | AN | 255 | Result Message | When Success 

&nbsp;

### Enterprise Credit Card Registration

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/onePass.do`
**Method** | POST
**Description** | Perform for Enterprise Credit Card Registration
**Merchant Token** | `SHA256(iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Request Parameters for Enterprise Credit Card Registration

```
    "iMid": "IONPAYTEST"
	"currency": "IDR"
	"amt": "10000"
	"instmntMon": "1"
	"referenceNo": "OrdNo-20190101010101"
	"goodsNm": "NICEPay Enterprise"
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
	"description": "NICEPay Enterprise Credit Card Registration"
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
	"cardCvv": "111"
	"recurrOpt": "2"
```

> Sample Cart Data Parameter for Enterprise Credit Card Registration (JSON)

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

> Setting Cart Data Parameter for Enterprise Credit Card Registration (JSON)

```json
    "cartData": "{\"count\": \"2\",\"item\": [{\"img_url\": \"http://img.aaa.com/ima1.jpg\",\"goods_name\": \"Item 1 Name\",\"goods_detail\": \"Item 1 Detail\",\"goods_amt\": \"700\"},{\"img_url\": \"http://img.aaa.com/ima2.jpg\",\"goods_name\": \"Item 2 Name\",\"goods_detail\": \"Item 2 Detail\",\"goods_amt\": \"300\"}]}"
```

**Request Parameters for Enterprise Credit Card Registration**

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
callBackUrl | &#8730; | AN | 255 | Payment Result Forward URL <br/> (on browser) 
dbProcessUrl | &#8730; | AN | 255 | Payment Notification URL <br/> (server side) 
vat | &nbsp; | N | 12 | Vat 
fee | &nbsp; | N | 12 | Service Fee 
notaxAmt | &nbsp; | N | 12 | Tax Free Amount 
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
instmntType | &#8730; | N | 2 | Installment Type, <br/> *Only for Credit Card `Installment`*, <br/> refer code at [Here](#installment-type) 
worker | &nbsp; | AN | 10 | Worker 
cartData | &#8730; | AN | 4000 | Cart Data 
cardCvv | &#8730; | N | 3 | Card CVV 
recurrOpt | &#8730; | N | 2 | Recurring Option, <br/> *Only for Credit Card `Recurring`*, <br/> refer code at [Here](#recurring-option) 

&nbsp;

**Cart Data Parameter for Enterprise E-Wallet Registration**

Parameter | Description 
---------- | ---------- 
count | Total card data count 
item | &nbsp; 
Item -> img_url | good's image URL <br/> (image size 50*50) 
Item -> goods_name | goods name 
Item -> goods_detail | goods detail description 
Item -> goods_amt | goods transaction amount

&nbsp;

> Sample Response Parameter for Enterprise Credit Card Registration (JSON)

```json
{
	"resultCd":"",
	"resultMsg":"",
	"tXid":"",
	"referenceNo":"",
	"payMethod":"",
	"amount":"",
	"currency":"",
	"goodsNm":"",
	"billingNm":"",
	"transDt":"",
	"transTm":"",
	"description":"",
	"callbackUrl":"",
	"authNo":"",
	"issuBankCd":"",
	"acquBankCd":"",
	"cardNo":"",
	"instmntMon":"",
	"instmntType":"",
	"recurringToken":"",
	"preauthToken":"",
	"ccTransType":"",
	"cardExpYymm":"",
	"issuBankNm":"",
	"acquBankNm":"",
	"vat":"",
	"fee":"",
	"notaxAmt":""
}
```

**Response Parameter for Enterprise Credit Card Registration**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
tXid | AN | 30 | Transaction ID <br/> (Key from NICEPay) | When Success 
referenceNo | ANS | 40 | Merchant Order No <br/> (Key from Merchant) | When Success 
payMethod | N | 2 | Payment Method, <br/> refer code at [Here](#payment-method) | When Success 
amount | N | 12 | Transaction Amount | When Success 
currency | AN | 3 | Currency | When Success 
goodsNm | AN | 100 | Goods Name | When Success 
billingNm | AN | 30 | Buyer Name | When Success 
transDt | N | 8 | Transaction Date <br/> (YYYYMMDD) | When Success 
transTm | N | 6 | Transaction Time <br/> (HH24MISS) | When Success 
description | AN | 100 | Transaction Description  | When Success 
callbackUrl | AN | 100 | Payment Result Forward URL <br/> (on browser) | When Success 
authNo | N | 10 | Authorization Number | When Success <br/> `Credit Card` 
issuBankCd | A | 4 | Issue Bank Code, <br/> refer code at [Here](#bank-code) | When Success <br/> `Credit Card` 
acquBankCd | A | 4 | Acquire Bank Code, <br/> refer code at [Here](#bank-code) | When Success <br/> `Credit Card` 
cardNo | AN | 20 | Card Number | When Success <br/> `Credit Card` 
instmntMon | N | 2 | Installment Month | When Success <br/> `Credit Card` 
instmntType | N | 2 | Installment Type, <br/> refer code at [Here](#installment-type) | When Success <br/> `Credit Card` 
recurringToken | AN | 64 | Token that using Recurring payment | When Success <br/> `Credit Card Recurring` 
preauthToken | AN | 64 | Token that using Capture process | When Success <br/> `Credit Card Pre-Auth` 
ccTransType | AN | 2 | Credit Card Transaction Type, <br/> refer code at [Here](#credit-card-transaction-type) | When Success <br/> `Credit Card` 
cardExpYymm | N | 4 | Card Expiry <br/> (YYMM) | When Success <br/> `Credit Card` 
issuBankNm | A | &nbsp; | Issue Bank Name | When Success <br/> `Credit Card` 
acquBankNm | A | &nbsp; | Acquire Bank Name | When Success <br/> `Credit Card` 
vat | N | 12 | Vat | When Success <br/> `Credit Card` 
fee | N | 12 | Service Fee | When Success <br/> `Credit Card` 
notaxAmt | N | 12 | Tax Free Amount | When Success <br/> `Credit Card` 