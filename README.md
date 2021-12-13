# USDT2UFI servise
USDT2UFI Docs

**Host:** https://exchange.purefi.io/api/

# To get rates:

Method: **/rates**   

Type: **GET**

Response Examle:

```

<rates>
    <item>
        <from>USDTTRC20</from>
        <to>UFI</to>
        <in>1.00000</in>
        <out>8.80752</out>
        <amount>91.45182</amount>
        <fromfee>0.0 USDTTRC20</fromfee>
        <tofee>0.0 UFI</tofee>
        <minamount>10.00000 USDTTRC20</minamount>
        <maxamount>91.45182 USDTTRC20</maxamount>
    </item>
    <item>
        <from>USDTERC20</from>
        <to>UFI</to>
        <in>1.00000</in>
        <out>8.80752</out>
        <amount>91.45182</amount>
        <fromfee>0.0 USDTERC20</fromfee>
        <tofee>0.0 UFI</tofee>
        <minamount>10.00000 USDTERC20</minamount>
        <maxamount>91.45182 USDTERC20</maxamount>
    </item>
</rates>

```

# To estimate exchange:

Metod: **/estimate**

type: **POST**

**Content-Type:** *application/json*

**Headers to Authorization:**
KEY   |    type
----- | -----
trustee-public-key:     |   *String*
trustee-timestamp:     |   *String*
trustee-signature:     |   *String*

**Body:** (--data-raw)
```
{
    "from": {currancy (USDTTRC20 or USDTTRC20)}
    "to": "BSC_UFI",
    "fromAmount": {amount in USDT}
} 
```

Response Examle:



**Response:**

Format | JSON
----- | -----
Success: |   { <br>  "from": "USDTTRC20", <br> "to": "BSC_UFI", <br> "fromAmount": 15.0055, <br> "toAmount": 88.6086810752545, <br> "fromRate": 1, <br> "toRate": 5.905080208940355, <br> "fromFee": 0, <br> "toFee": 0, <br> "extraFromFee": 0, <br> "extraToFee": 0, <br> "fromRevenueShare": 0, <br> "toRevenueShare": 0, <br> "rateType": "FLOATING" <br> }
Error: |  {  <br>  "errorCode": `ERROR_CODE`, <br>  "message": ```error message```}

# To exchange:

Metod: **/place**

type: **POST**

**Content-Type:** *application/json*

**Headers to Authorization:**
KEY   |    type
----- | -----
trustee-public-key:     |   *String*
trustee-timestamp:     |   *String*
trustee-signature:     |   *String*

**Body:** (--data-raw)
```
{
    "from": {currancy (USDTTRC20 or USDTTRC20)}
    "to": "BSC_UFI",
    "fromAmount": {amount in USDT}
    "toPaymentDetails": {addres for UFIBEP20}
} 
```

Response Examle:



**Response:**

Format | JSON
----- | -----
Success: |   { <br>  "id": "163a9ff7c4996793c0321c606149c2f6", <br>  "from": "USDTERC20", <br>  "to": "BSC_UFI", <br>  "fromAmount": 15.00555, <br>  "toAmount": 88.2535246, <br>  "status": "WAITING", <br>  "fromPaymentDetails": "", <br>  "toPaymentDetails": "0x5CcBCf9a648d5194106dAbFB42918B29971dd740", <br>  "payCryptoAddress": "0x69dA9343ba5e42A996Ba69422059ed1F445E78aD", <br>  "fromTxHash": "", <br>  "toTxHash": null, <br>  "rateType": "FLOATING", <br>  "userId": "", <br>  "payCryptoMemo": "", <br>  "toMemo": "", <br>  "extraFromFee": 0, <br>  "extraToFee": 0, <br>  "fromFee": 0, <br>  "toFee": 0, <br>  "fromRevenueShare": 0, <br>  "toRevenueShare": 0 <br>  }
Error: |  {  <br>  "errorCode": `ERROR_CODE`, <br>  "message": ```error message```}

Error Examle:
{
    "errorCode": "PROVIDER_ERROR",
    "message": "Unsupported TO asset code"
}
# To get order status:

Method: **/order**   

Type: **GET**

**Query Param:** id
from [Place response]() 
` order/?id= `

Response Examle:

```
 {
    "id": "163a9ff7c4996793c0321c606149c2f6",
    "from": "USDTERC20",
    "to": "BSC_UFI",
    "fromAmount": 15.00555,
    "toAmount": 88.2535246,
    "status": "WAITING",
    "fromPaymentDetails": "",
    "toPaymentDetails": "0x5CcBCf9a648d5194106dAbFB42918B29971dd740",
    "payCryptoAddress": "0x69dA9343ba5e42A996Ba69422059ed1F445E78aD",
    "fromTxHash": "",
    "toTxHash": null,
    "rateType": "FLOATING",
    "userId": "",
    "payCryptoMemo": "",
    "toMemo": "",
    "extraFromFee": 0,
    "extraToFee": 0,
    "fromFee": 0,
    "toFee": 0,
    "fromRevenueShare": 0,
    "toRevenueShare": 0
}
```
