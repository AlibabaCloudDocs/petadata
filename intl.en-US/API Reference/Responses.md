# Responses {#concept_fvv_gw4_mfb .concept}

After an API operation is called, data is returned in a unified format. An HTTP status code that starts with `2xx` indicates that the call is successful. An HTTP status code that starts with `4xx` or `5xx` indicates that the call fails.

For a successful request, data is usually returned in XML or JSON format. When you call an API, you can specify the format of the returned data in the request parameters. The default format is XML. To make the responses more reader-friendly, the format of the sample responses in this topic is slightly adjusted. The actual responses are not formatted with line breaks or indentation.

## Successful responses {#section_khb_jjy_gbb .section}

**XML format**

The responses in XML format include information about whether the call was successful, and details specific to the operation. Example:

```
<? xml version="1.0" encoding="utf-8"? >  
<!—The root node of the result--> 
<API name+Response> 
    <!—Request tag returned--> 
 <RequestId>xxxxxxxxx</RequestId> 
    <!—Returned data--> 
</API name+Response>
```

**JSON format**

```screen
{ 
    "RequestId": "xxxxxxxxx"
    /*Returned data*/
}
```

## Error responses {#section_ovt_ljy_gbb .section}

No result is returned if an error occurs while calling an operation. To identify the cause of an error, see [Error codes](reseller.en-US/API Reference/Appendix/Error codes/Client error codes.md#) in Appendix.

If an error occurs while calling an API over HTTP, an HTTP status code that starts with `4xx` or `5xx` is returned. The returned message contains the specific error code and error message. It also contains a globally unique request ID \(RequestId\) and the ID of the site you accessed with this request \(HostId\). If you cannot identify the cause of the error, contact Alibaba Cloud customer service and provide your HostId and RequestId so that we can solve the problem as soon as possible.

**XML format**

```
<? xml version="1.0" encoding="UTF-8"? > 
<Error> 
   <RequestId>xxxxxxxxxxxxxxxxxxx</RequestId> 
   <HostId>petadata.aliyuncs.com</HostId> 
   <Code>UnsupportedOperation</Code> 
   <Message>"This specified action is not valid</Message> 
</Error> 
```

**JSON format**

```screen
{ 
"RequestId": "xxxxxxxxxxxxxxxxxxx", 
"HostID": "petadata.aliyuncs.com ", 
"Code": "UnsupportedOperation", 
    "Message": "This specified action is not valid"
} 

```

