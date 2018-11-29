# Common parameters {#concept_ghx_fw4_mfb .concept}

## Common request parameters { .section}

Common request parameters refer to the required parameters in each API.

|Name|Type|Required|Description|
|----|----|--------|-----------|
|Format|String|Yes|The format of the response. JSON and XML formats are supported.|
|Version|String|Yes|The version of the APIs. The version is in date format: YYYY-MM-DD. The current version is 2016-01-01.|
|AccessKeyId|String|Yes|The AccessKey ID issued by Alibaba Cloud, which is used for calling operations.|
|Signature|String|Yes|The signature, which is used for signing requests.|
|SignatureMethod|String|Yes|The signature method. Currently, HMAC-SHA1 is supported.|
|Timestamp|String|Yes|The timestamp of the request signature. The timestamp must follow ISO 8601 format: `yyyy-MM-ddTHH:mm:ssZ`.|
|SignatureVersion|String|Yes|The signature version. The current version is 1.0.|
|SignatureNonce|String|Yes|A random number, which is used to prevent replay attacks.|

**Examples**

```
https://petadata.aliyuncs.com/
?Format=xml 
&Version=2013-08-15 
&Signature=Pc5WB8gokVn0xfeu%2FZV%2BiNM1dgI%3D  
&SignatureMethod=HMAC-SHA1 
&SignatureNonce=15215528852396 
&SignatureVersion=1.0 
&AccessKeyId=key-test 
&Timestamp=2013-06-01T12:00:00Z
&<Request parameters specific to the operation>

```

## Common response parameters {#section_hs4_m3y_gbb .section}

Every time you send a request to call an operation, whether the request is successful or not, the system returns a unique identification code \(RequestId\) .

Example:

```

<? xml version="1.0" encoding="utf-8"? > 
<!—The root node of the result--> 
<API name+Response> 
<!—The request tag returned--> 
<RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId> 
</API name+Response>

```

JSON

```
 
{ 
"RequestId": "4C467B38-3910-447D-87BC-AC049166F216", 
/* Returned data*/ 
}

```

