# Notification 

<aside class="notice">If your system use firewall, add allow policy for NICEPay IP</aside>

Description | Value
---------- | ----------
Development Environment | `103.20.51.39` 
Production Environment | `103.20.51.34`

&nbsp; | &nbsp;
---------- | ----------
**API url** | `dbProcessUrl on Registration API Request`
**Method** | POST
**Description** | Transaction Result Notification (When Success)
**Merchant Token** | `SHA256(iMid + tXid + amt + merchantKey)`

&nbsp;

> Sample Parameter Notification (POST)

```
// Common Parameter Notification
tXid = {tXid}
referenceNo = {referenceNo}
payMethod = {payMethod}
amt = {amt}
transDt = {transDt}
transTm = {transTm}
currency = {currency}
goodsNm = {goodsNm}
billingNm = {billingNm}
matchCl = {matchCl}
status = {status}
merchantToken = {merchantToken}

// Additional Parameter for Credit Card Notification
authNo = {authNo}
issuBankCd = {issuBankCd}
acquBankCd = {acquBankCd}
cardNo = {cardNo}
instmntMon = {instmntMon}
instmntType = {instmntType}
preauthToken = {preauthToken}
recurringToken = {recurringToken}
ccTransType = {ccTransType}
cardExpYymm = {cardExpYymm}
issuBankNm = {issuBankNm}
acquBankNm = {acquBankNm}
vat = {vat}
fee = {fee}
notaxAmt = {notaxAmt}

// Additional Parameter for Virtual Account Notification
bankCd = {bankCd}
vacctNo = {vacctNo}
vacctValidDt = {vacctValidDt}
vacctValidTm = {vacctValidTm}

// Additional Parameter for Other Payment Method Notification
mitraCd = {mitraCd}
payNo = {payNo}
payValidDt = {payValidDt}
payValidTm = {payValidTm}
receiptCode = {receiptCode}
mRefNo = {mRefNo}
```

**Common Parameter Notification**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
tXid | AN | 30 | Transaction Id (Key from NICEPay) | &nbsp;
referenceNo | ANS | 40 | Merchant Order No (Key from merchant) | &nbsp;
payMethod | N | 2 | Payment Method, <br/> refer Code at [Here](#payment-method) | &nbsp;
amt | N | 12 | Payment Amount | &nbsp;
transDt | N | 8 | Transaction Date (YYYYMMDD) | &nbsp;
transTm | N | 6 | Transaction Time (HH24MISS) | &nbsp;
currency | AN | 3 | Currency | &nbsp;
goodsNm | AN | 100 | Goods Name | &nbsp;
billingNm | A | 30 | Buyer Name | &nbsp;
matchCl | N | 1 | Payment Amount Match Flag, <br/> refer Code at [Here](#notification-match-amount-indicator) | &nbsp;
status | N | 1 | Deposit Status, <br/> refer Code at [Here](#notification-status-code) | &nbsp;
merchantToken | AN | 255 | Merchant Token | &nbsp;

&nbsp;

**Additional Parameter for Credit Card Notification**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
authNo | N | 10 | Approval Number | &nbsp; 
issuBankCd | A | 4 | Issue Bank Code | &nbsp; 
acquBankCd | A | &nbsp; | Acquire Bank Code | &nbsp; 
cardNo | AN | 20 | Card No With Masking | &nbsp; 
instmntMon | N | 2 | Installment Month | &nbsp; 
instmntType | N | 2 | Installment Type, <br/> refer Code at [Here](#installment-type) | &nbsp; 
preauthToken | AN | 255 | Pre-Auth Token (need for capture) | &nbsp; 
recurringToken | AN | 255 | Recurring Token (can use next payment) | &nbsp; 
ccTransType | AN | 2 | Credit Card Transaction Type, <br/> refer Code at [Here](#credit-card-transaction-type) | &nbsp; 
cardExpYymm | N | &nbsp; | Card Expiry (YYMM) | &nbsp; 
issuBankNm | A | 4 | Issue Bank Name | &nbsp; 
acquBankNm | A | &nbsp; | Acquire Bank Name | &nbsp; 
vat | N | 12 | Vat | &nbsp; 
fee | N | 12 | Service Fee | &nbsp; 
notaxAmt | N | 12 | Tax Free Amount | &nbsp; 

&nbsp;

**Additional Parameter for Virtual Account Notification**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
bankCd | AN | 4 | Bank Code, <br/> refer Code at [Here](#bank-code) | &nbsp; 
vacctNo | N | 16 | Bank Virtual Account Number | &nbsp; 
vacctValidDt | N | 8 | Virtual Account Expiry Date (YYYYMMDD) | &nbsp; 
vacctValidTm | N | 6 | Virtual Account Expiry Time (HH24MISS) | &nbsp; 

&nbsp;

**Additional Parameter for Other Payment Method Notification**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
mitraCd | A | 4 | Mitra Code, <br/> refer Code at [Here](#mitra-code) | &nbsp; 
payNo | N | 12 | Convenience Store Number | &nbsp; 
payValidDt | N | 8 | Convenience Store Expiry Date (YYYYMMDD) | &nbsp; 
payValidTm | N | 6 | Convenience Store Expiry Time (HH24MISS) | &nbsp; 
receiptCode | ANS | 20 | Authorization Number | &nbsp; 
mRefNo | AN | 18 | Bank Reference No | &nbsp; 