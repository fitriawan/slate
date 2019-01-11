# Order Inquiry

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/onePassStatus.do`
**Method** | POST
**Description** | Perform for Order Inquiry
**Merchant Token** | `SHA256(timeStamp + iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Response Parameter for Order Inquiry (JSON)

```
	timeStamp = 
	tXid = 
	iMid = 
	referenceNo = 
	amt = 
	merchantToken = 
```

**Request Parameters for Order Inquiry**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- 
timeStamp | &#8730; | N | 14 | API Request Date 
tXid | &#8730; | AN | 30 | Transaction Id 
iMid | &#8730; | AN | 10 | Merchant Id 
referenceNo | &#8730; | ANS | 40 | Merchant Order No 
amt | &#8730; | N | 12 | Transaction  Amount 
merchantToken | &#8730; | AN | 255 | Merchant Token 

&nbsp;

> Sample Response Parameter for Order Inquiry (JSON)

```json
{
	// Common Response Parameter Order Inquiry
	"resultCd": "0000",
	"resultMsg": "SUCCESS",
	"tXid": "",
	"iMid": "",
	"referenceNo": "",
	"payMethod": "",
	"amt": "",
	"cancelAmt": "",
	"reqDt": "",
	"reqTm": "",
	"transDt": "",
	"transTm": "",
	"depositDt": "",
	"depositTm": "",
	"currency": "",
	"goodsNm": "",
	"billingNm": "",
	"status": "",

	// Additional Response Parameter for Credit Card Order Inquiry
	"authNo": "",
	"issuBankCd": "",
	"issuBankNm": "",
	"acquBankCd": "",
	"acquBankNm": "",
	"cardNo": "",
	"cardExpYymm": "",
	"instmntMon": "",
	"instmntType": "",
	"preauthToken": "",
	"recurringToken": "",
	"ccTransType": "",
	"acquStatus": "",
	"vat": "",
	"fee": "",
	"notaxAmt": "",

	// Additional Response Parameter for Virtual Account Order Inquiry
	"bankCd": "",
	"vacctNo": "",
	"vacctValidDt": "",
	"vacctValidTm": "",

	// Additional Response Parameter for Other Payment Method Order Inquiry
	"mitraCd": "",
	"payNo": "",
	"payValidTm": "",
	"payValidDt": "",
	"receiptCode": "",
	"mRefNo": "" 
}
```

**Common Response Parameter Order Inquiry**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
tXid | AN | 30 | Transaction Id <br/> (Key from NICEPay) | &nbsp; 
iMid | AN | 10 | Merchant Id | &nbsp; 
referenceNo | ANS | 40 | Merchant Order No <br/> (Key from merchant) | &nbsp; 
payMethod | N | 2 | Payment Method, <br/> refer Code at [Here](#payment-method) | &nbsp; 
amt | N | 12 | Payment Amount | &nbsp; 
cancelAmt | N | 12 | Cancel Amount | &nbsp; 
reqDt | N | 8 | Transaction Request Date <br/> (YYYYMMDD) | &nbsp; 
reqTm | N | 6 | Transaction Request Time <br/> (HH24MISS) | &nbsp; 
transDt | N | 8 | Transaction Date <br/> (YYYYMMDD) | &nbsp; 
transTm | N | 6 | Transaction Time <br/> (HH24MISS) | &nbsp; 
depositDt | N | &nbsp; | Transaction Deposit Date | &nbsp; 
depositTm | N | &nbsp; | Transaction Deposit Time | &nbsp; 
currency | AN | 3 | Currency | &nbsp; 
goodsNm | AN | 100 | Goods Name | &nbsp; 
billingNm | AN | 30 | Buyer Name | &nbsp; 
status | N | 1 | Transaction Status, <br/> refer Code at [Here](#status-code) | &nbsp; 

&nbsp;

**Additional Response Parameter for Credit Card Order Inquiry**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
authNo | N | 10 | Approval Number | &nbsp; 
issuBankCd | A | 4 | Issue Bank Code, <br/> refer Code at [Here](#bank-code) | &nbsp; 
acquBankCd | A | 4 | Acquire Bank Code, <br/> refer Code at [Here](#bank-code) | &nbsp; 
cardNo | AN | 20 | Card No With Masking | &nbsp; 
instmntMon | N | 2 | Installment Month | &nbsp; 
instmntType | N | 2 | Installment Type, <br/> refer Code at [Here](#installment-type) | &nbsp; 
preauthToken | AN | 255 | Pre-Auth Token <br/> (need for capture) | &nbsp; 
recurringToken | AN | 255 | Recurring Token <br/> (Can use next payment) | &nbsp; 
ccTransType | AN | 2 | Credit Card Transaction Type, <br/> refer Code at [Here](#credit-card-transaction-type) | &nbsp; 
acquStatus | AN | 2 | Purchase Status, <br/> refer Code at [Here](#purchase-status) | &nbsp; 
cardExpYymm | N | 4 | Card Expiry <br/> (YYMM) | &nbsp; 
issuBankNm | A | &nbsp; | Issue Bank Name | &nbsp; 
acquBankNm | A | &nbsp; | Acquire Bank Name | &nbsp; 
vat | N | 12 | Vat | &nbsp; 
fee | N | 12 | Service Fee | &nbsp; 
notaxAmt | N | 12 | Tax Free Amount | &nbsp; 

&nbsp;

**Additional Response Parameter for Virtual Account Order Inquiry**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
bankCd | AN | 4 | Bank Code, <br/> refer Code at [Here](#bank-code) | &nbsp; 
vacctNo | N | 16 | Bank Virtual Account Number | &nbsp; 
vacctValidDt | N | 8 | Virtual Account Expiry Date <br/> (YYYYMMDD) | &nbsp; 
vacctValidTm | N | 6 | Virtual Account Expiry Time <br/> (HH24MISS) | &nbsp; 

&nbsp;

**Additional Response Parameter for Other Payment Method Order Inquiry**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
mitraCd | A | 4 | Mitra code, refer Code at [Here](#mitra-code) | &nbsp;
payNo | N | 12 | Convenience Store Number | &nbsp;
payValidDt | N | 8 | Convenience Store Expiry Date <br/> (YYYYMMDD) | &nbsp;
payValidTm | N | 6 | Convenience Store Expiry Time <br/> (HH24MISS) | &nbsp;
receiptCode | ANS | 20 | Authorization Number | &nbsp;
mRefNo | AN | 18 | Bank Reference No | &nbsp; 