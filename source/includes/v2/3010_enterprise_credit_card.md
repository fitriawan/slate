## Enterprise Credit Card

### Enterprise Credit Card Flow

![NICEPay API v2 Enterprise Credit Card Flow](/images/v2/ent/flow/3010_enterprise_credit_card_flow.jpg "NICEPay API v2 Enterprise Credit Card Flow")

&nbsp;

### Enterprise Credit Card Registration

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://api.nicepay.co.id/nicepay/direct/v2/registration`
**Method** | POST, JSON
**Description** | Perform for Enterprise Credit Card Registration
**Merchant Token** | `SHA256(timeStamp + iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Request Parameter for Enterprise Credit Card Registration (JSON)

```json
{
	"timeStamp": "20190101010101",
	"iMid": "IONPAYTEST",
	"payMethod": "01",
	"currency": "IDR",
	"amt": "10000",
	"referenceNo": "OrdNo-20190101010101",
	"goodsNm": "NICEPay Enterprise",
	"billingNm": "John Doe",
	"billingEmail": "customer@merchant.com",
	"billingPhone": "08123456789",
	"billingAddr": "Jl. Casablanca Raya Kav 88",
	"billingCity": "Jakarta",
	"billingState": "Jakarta Selatan",
	"billingPostCd": "12345",
	"billingCountry": "Indonesia",
	"deliveryNm": "Jane Doe",
	"deliveryPhone": "08123456789",
	"deliveryAddr": "Jl. Casablanca Raya Kav 88",
	"deliveryCity": "Jakarta",
	"deliveryState": "Jakarta Selatan",
	"deliveryPostCd": "12345",
	"deliveryCountry": "Indonesia",
	"dbProcessUrl": "https://merchant.com/notification",
	"vat": "0",
	"fee": "0",
	"notaxAmt": "0",
	"description": "NICEPay Enterprise Credit Card Registration",
	"userIP": "127.0.0.1",
	"merchantToken": "",
	"cartData": "{}",
	"reqDt": "20190101",
	"reqTm": "010101",
	"reqDomain": "https://merchant.com",
	"reqServerIP": "127.0.0.1",
	"reqClientVer": "1.0",
	"userSessionID": "",
	"userAgent": "Mozilla",
	"userLanguage": "en-US",
	"instmntMon": "1",
	"instmntType": "2",
	"recurrOpt": "2",
	"worker": "John Doe"
}
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
{
    "cartData": "{\"count\": \"2\",\"item\": [{\"img_url\": \"http://img.aaa.com/ima1.jpg\",\"goods_name\": \"Item 1 Name\",\"goods_detail\": \"Item 1 Detail\",\"goods_amt\": \"700\"},{\"img_url\": \"http://img.aaa.com/ima2.jpg\",\"goods_name\": \"Item 2 Name\",\"goods_detail\": \"Item 2 Detail\",\"goods_amt\": \"300\"}]}"
}
```

**Request Parameter for Enterprise Credit Card Registration**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
timeStamp | &#8730; | N | 14 | API Request Date 
iMid | &#8730; | AN | 10 | Merchant ID 
payMethod | &#8730; | AN | 2 | Payment Method, <br/> refer code at [Here](#payment-method) 
currency | &#8730; | AN | 3 | Currency 
amt | &#8730; | N | 12 | Goods Amount 
referenceNo | &#8730; | ANS | 40 | Merchant Order No 
goodsNm | &#8730; | AN | 100 | Goods Name 
billingNm | &#8730; | A | 30 | Buyer Name 
billingEmail | &#8730; | AN | 40 | Buyer Email 
billingPhone | &#8730; | N | 15 | Buyer Phone Number 
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
dbProcessUrl | &#8730; | AN | 255 | Payment Notification Url <br/> (server side) 
vat | &nbsp; | N | 12 | Vat 
fee | &nbsp; | N | 12 | Service Fee 
notaxAmt | &nbsp; | N | 12 | Tax Free Amount 
description | &nbsp; | AN | 100 | Transaction Description 
userIP | &#8730; | AN | 15 | User IP <br/> (customer) 
merchantToken | &#8730; | AN | 255 | Merchant Token 
cartData | &#8730; | AN | 4000 | Cart Data 
reqDt | &nbsp; | N | 8 | Request Date <br/> (YYYYMMDD) 
reqTm | &nbsp; | N | 6 | Request Time <br/> (HH24MISS) 
reqDomain | &nbsp; | AN | 100 | Request Domain 
reqServerIP | &nbsp; | AN | 15 | Request Server IP 
reqClientVer | &nbsp; | AN | 50 | Request Client Version 
userSessionID | &nbsp; | AN | 100 | User Session ID 
userAgent | &nbsp; | AN | 100 | User Agent Information 
userLanguage | &nbsp; | A | 2 | User Language 
instmntMon | &#8730; | N | 2 | Installment Month 
instmntType | &#8730; | N | 2 | Installment Type, <br/> refer code at [Here](#installment-type) 
recurrOpt | &#8730; | N | 2 | Recurring Option, <br/> refer code at [Here](#recurring-option) 
worker | &nbsp; | AN | 10 | Worker 

&nbsp;

**Cart Data Parameter for Enterprise Credit Card Registration**

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
	"resultCd": "0000",
    "resultMsg": "SUCCESS",
    "tXid": "",
    "referenceNo": "",
    "payMethod": "",
    "amt": "",
    "transDt": "",
    "transTm": "",
    "description": "",
    "bankCd": "",
    "vacctNo": "",
    "mitraCd": "",
    "payNo": "",
    "currency": "",
    "goodsNm": "",
    "billingNm": "",
    "vacctValidDt": "",
    "vacctValidTm": "",
    "payValidDt": "",
    "payValidTm": ""
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
amt | N | 12 | Payment Amount | When Success 
transDt | N | 8 | Transaction Date <br/> (YYYYMMDD) | When Success 
transTm | N | 6 | Transaction Time <br/> (HH24MISS) | When Success 
description | AN | 100 | Transaction Description | When Success 
bankCd | A | 4 | Bank Code <br/> refer Code at [Here](#bank-code) | When Success <br/> `Virtual Account`
vacctNo | N | 20 | Virtual Account Number | When Success <br/> `Virtual Account`
mitraCd | AN | 4 | Mitra Code <br/> refer Code at [Here](#mitra-code) | When Success <br/> `Convenience Store`
payNo | N | 12 | Convenience Store Number | When Success <br/> `Convenience Store`
currency | AN | 3 | Currency | When Success 
goodsNm | AN | 100 | Goods Name | When Success 
billingNm | A | 30 | Buyer Name | When Success 
vacctValidDt | N | 8 | Virtual Account Expiry Date <br/> (YYYYMMDD) | When Success <br/> `Virtual Account`
vacctValidTm | N | 6 | Virtual Account Expiry Time <br/> (HH24MISS) | When Success <br/> `Virtual Account`
payValidDt | N | 8 | Convenience Store Expiry Date <br/> (YYYYMMDD) | When Success <br/> `Convenience Store`
payValidTm | N | 6 | Convenience Store Expiry Time <br/> (HH24MISS) | When Success <br/> `Convenience Store`

&nbsp;

### Enterprise Credit Card Payment

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://api.nicepay.co.id/nicepay/direct/v2/payment`
**Method** | POST
**Description** | Perform for Enterprise Credit Card Payment
**Merchant Token** | `SHA256(timeStamp + iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Request Parameter for Enterprise Credit Card Payment

```
	"timeStamp": ""
	"tXid": ""
	"cardNo": ""
	"cardExpYymm": ""
	"cardCvv": ""
	"recurringToken": ""
	"preauthToken": ""
	"clickPayNo": ""
	"dataField3": ""
	"clickPayToken": ""
	"merchantToken": ""
	"callBackUrl": ""
	"cardHolderNm": ""
```

**Request Parameter for Enterprise Credit Card Payment**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
timeStamp | &#8730; | N | 14 | API Request Date 
tXid | &#8730; | AN | 30 | Transaction ID 
cardNo | &#8730; | N | 20 | Full Card Number <br/> Mandatory `Credit Card` 
cardExpYymm | &#8730; | N | 4 | Card Expiry <br/> (YYMM) <br/> Mandatory `Credit Card` 
cardCvv | &#8730; | N | 4 | Card CVV <br/> Mandatory `Credit Card` 
recurringToken | &#8730; | AN | 64 | Recurring Token <br/> Mandatory `Credit Card Recurring` 
preauthToken | &#8730; | AN | 64 | Pre-Auth Token <br/> Mandatory `Credit Card Pre-Auth` 
clickPayNo | &#8730; | N | 16 | ClickPay Number <br/> Mandatory `ClickPay` 
dataField3 | &#8730; | N | 16 | Token Input 3 for ClickPay <br/> Mandatory `ClickPay` 
clickPayToken | &#8730; | N | 6 | Code Response from Token <br/> Mandatory `ClickPay` 
merchantToken | &#8730; | AN | 255 | Merchant Token 
callBackUrl | &#8730; | AN | 255 | Payment Result Forward URL <br/> (on browser) 
cardHolderNm | &#8730; | AN | 50 | Card Holder Name <br/> Mandatory `Credit Card CIMB` 

&nbsp;

> Sample Response Parameter for Enterprise Credit Card Payment

```
callBackUrl?resultCd=0000&resultMsg=SUCCESS&tXid=&referenceNo=OrdNo-&payMethod=&amt=&transDt=&transTm=&description=&authNo=&issuBankCd=&acquBankCd=&issuBankNm=&acquBankNm=&cardNo=&receiptCode=&mitraCd=&recurringToken=&preauthToken=&currency=&goodsNm=&billingNm=&ccTransType=&mRefNo=&instmntMon=&instmntType=&cardExpYymm=&vat=&fee=&notaxAmt=&timeStamp=&merchantToken=
```

**Response Parameter for Enterprise Credit Card Payment**

Parameter | Type | Size | Description | Remark 
---------- | ---------- | ---------- | ---------- | ---------- 
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
tXid | AN | 30 | Transaction ID <br/> (Key from NICEPay) | When Success 
referenceNo | ANS | 40 | Merchant Order No <br/> (Key from Merchant) | When Success 
payMethod | N | 2 | Payment Method | When Success 
amt | N | 12 | Payment Amount | When Success 
transDt | N | 8 | Transaction Date <br/> (YYYYMMDD) | When Success 
transTm | N | 6 | Transaction Time <br/> (HH24MISS) | When Success 
description | AN | 100 | Transaction Description | When Success 
authNo | N | 10 | Approval Number | When Success <br/> `Credit Card`
issuBankCd | A | 4 | Issuer Bank Code | When Success <br/> `Credit Card`
acquBankCd | A | 4 | Acquire Bank Code | When Success <br/> `Credit Card`
issuBankNm | &nbsp; | &nbsp; | Issuer Bank Name | When Success <br/> `Credit Card`
acquBankNm | &nbsp; | &nbsp; | Acquire Bank Name | When Success <br/> `Credit Card`
cardNo | AN | 20 | Card No With Masking | When Success <br/> `Credit Card`
receiptCode | ANS | 20 | Authorization Number | When Success <br/> `ClickPay`
mitraCd | AN | 4 | Mitra Code | When Success <br/> `ClickPay`, `E-Wallet`
recurringToken | AN | 64 | Token That Using Recurring Payment | When Success <br/> `Credit Card Recurring`
preauthToken | AN | 64 | Token That Using Capture Process | When Success <br/> `Credit Card Pre-Auth`
currency | AN | 3 | Currency | When Success 
goodsNm | AN | 100 | Goods Name | When Success 
billingNm | AN | 30 | Buyer Name | When Success 
ccTransType | AN | 2 | Credit Card Transaction Type | When Success <br/> `Credit Card`
mRefNo | AN | 18 | Bank Reference No | When Success <br/> `ClickPay`
instmntMon | N | 2 | Installment Month | When Success <br/> `Credit Card`
instmntType | N | 2 | Installment Type | When Success <br/> `Credit Card`
cardExpYymm | N | 4 | Card Expiry <br/> (YYMM) | When Success <br/> `Credit Card`
vat | N | 12 | Vat | When Success <br/> `Credit Card`
fee | N | 12 | Service Fee | When Success <br/> `Credit Card`
notaxAmt | N | 12 | Tax Free Amount | When Success <br/> `Credit Card`
timeStamp | N | 14 | Response Date | When Success 
merchantToken | AN | 255 | Merchant Token | When Success 