# Cancel

&nbsp; | &nbsp;
---------- | ----------
**API url** | `https://www.nicepay.co.id/nicepay/api/onePassAllCancel.do`
**Method** | POST
**Description** | Perform for Cancel Transaction `Credit Card`, `Virtual Account`, `Convenience Store`
**Merchant Token** | `SHA256(timeStamp + iMid + referenceNo + amt + merchantKey)`

&nbsp;

> Sample Response Parameter for Cancel (JSON)

```
	timeStamp = 
	tXid = 
	iMid = 
	payMethod = 
	cancelType = 
	cancelMsg = 
	merchantToken = 
	preauthToken = 
	amt = 
	fee = 
	vat = 
	notaxAmt = 
	cancelServerIp = 
	cancelUserId = 
	cancelUserIp = 
	cancelUserInfo = 
	cancelRetryCnt = 
	worker = 
```

**Request Parameters for Cancel**

Parameter | Mandatory | Type | Size | Description 
---------- | ---------- | ---------- | ---------- | ---------- | ---------- 
timeStamp | &#8730; | N | 14 | API Request Date 
tXid | &#8730; | AN | 30 | Transaction Id 
iMid | &#8730; | AN | 10 | Merchant Id 
payMethod | &#8730; | N | 2 | Payment Method, <br/> refer Code at [Here](#payment-method) 
cancelType | &#8730; | N | 2 | Cancel Type, <br/> refer Code at [Here](#cancel-type) 
cancelMsg | &nbsp; | AN | 255 | Cancel Message 
merchantToken | &#8730; | AN | 255 | Merchant Token 
preauthToken | &#8730; | AN | 100 | Preauth Token <br/> Mandatory `Credit Card Pre-Auth`
amt | &#8730; | N | 12 | Payment Amount 
fee | &nbsp; | N | 12 | Fee 
vat | &nbsp; | N | 12 | Vat 
notaxAmt | &nbsp; | N | 12 | No Tax Amount 
cancelServerIp | &nbsp; | AN | 15 | Server Ip 
cancelUserId | &nbsp; | AN | 30 | User Id 
cancelUserIp | &nbsp; | AN | 15 | User Ip 
cancelUserInfo | &nbsp; | AN | 100 | User Information 
cancelRetryCnt | &nbsp; | N | 2 | Retry Count 
worker | &nbsp; | AN | 10 | Worker 

&nbsp;

> Sample Response Parameter for Cancel (JSON)

```json
{
	"resultCd":"",
	"resultMsg":"",
	"tXid":"",
	"canceltXid":"",
	"referenceNo":"",
	"amt":"",
	"description":"",
	"transDt":"",
	"transTm":""
}
```

**Response Parameter for Cancel**

Parameter | Type | Size | Description | Remark
---------- | ---------- | ---------- | ---------- | ----------
resultCd | N | 4 | Result Code | &nbsp; 
resultMsg | AN | 255 | Result Message | &nbsp; 
tXid | AN | 30 | Transaction Id | When Succes 
canceltXid | AN | 30 | Cancel Transaction Id | When Success 
referenceNo | ANS | 40 | Merchant Order No | When Succes 
amt | N | 12 | Amount | When Succes 
description | AN | 255 | Description | When Succes 
transDt | N | 8 | Transaction Date | When Succes 
transTm | N | 6 | Transaction Time | When Succes 