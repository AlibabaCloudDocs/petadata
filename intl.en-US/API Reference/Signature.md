# Signature {#concept_cws_hw4_mfb .concept}

HybridDB for MySQL performs identity authentication on each access request. Therefore, whether submitted through HTTP or HTTPS, a request must contain signature information. HybridDB for MySQL uses symmetric encryption based on an AccessKey \(AccessKey ID and AccessKey Secret\) to verify the identity of request senders. The AccessKey is issued to users by Alibaba Cloud. You can generate and manage the AccessKey on the Alibaba Cloud website. The AccessKey ID indicates the identity of the user. The AccessKey Secret is the key used to encrypt the signature string and to verify the signature string on the server. It must be kept strictly confidential and only be known to Alibaba Cloud and authenticated users.

Follow these instructions to sign your requests.

1.  Use request parameters to construct a canonical query string.
    1.  Sort all request parameters \(including common request parameters and parameters specific to the API, but excluding the Signature parameter mentioned in common request parameters\) in alphabetical order.

        **Note:** When you submit a request using the GET method, these parameters form a part of the request URI. In the request URI, the parameters are placed after the question mark \(?\) and are connected by the ampersand \(&\).

    2.  Encode the name and value of each request parameter. The name and value are encoded using the UTF-8 character set. The rules for URL encoding are as follows:

        -   Do not encode any of the unreserved characters including A-Z, a-z, 0-9, en dashes \(-\), underscores \(\_\), periods \(.\), and tildes \(~\).
        -   Percent encode all other characters with %XY, where X and Y are corresponding hexadecimal ASCII values. The quotation mark \("\) is encoded as %22 .
        -   Percent encode extended UTF-8 characters in the form of %XY%ZA.
        -   An English space is encoded as %20, rather than the plus sign \(+\).
        **Note:** NoticeGenerally, libraries supporting the URL encoding \(for example, java.net.URLEncoder in Java\) are all encoded according to the rules for `application/x-www-form-urlencoded` of the MIME type. You can use this encoding method by replacing the plus sign \(+\) in the encoded string with "%20", replacing the asterisk \(\*\) with "%2A", and changing "%7E" back to the tilde \(~\) .

    3.  Connect the encoded parameter names and values with equal signs \(=\).
    4.  Sort the equal sign-connected strings in alphabetical order, connect them with ampersands \(&\), and you obtain a canonical query string.
2.  Use the canonical query string to build a string for signature calculation:

    ```
    StringToSign= HTTPMethod + "&" + percentEncode("/") + "&" + 
                            percentEncode(CanonicalizedQueryString) 
                        
    ```

    HTTPMethod: the HTTP method used to submit the request, such as GET.

    percentEncode\("/"\): the value for the character "/"coded according to the URL encoding rules described in 1.b, which is "%2F".

    percentEncode\(CanonicalizedQueryString\): the canonical query string \(constructed in the first step\) that is encoded according to the URL encoding rules described in 1.b.

3.  Use the StringToSign to calculate the HMAC value of the signature based on [RFC2104](http://www.ietf.org/rfc/rfc2104.txt).

    **Note:** When the signature is calculated, the key is the AccessKey Secret held by the user followed by the ampersand \(&\) character \(ASCII code:38\), and the SHA1 hash algorithm is used.

4.  Encode the HMAC value into a string based on Base64 encoding rules to obtain the signature.
5.  Add the obtained signature to request parameters as the Signature parameter to complete the request signing process.

    **Note:** 

    When the obtained signature value is submitted to the HybridDB for MySQL server as the final request parameter value, the URL encoding must be performed for the value in compliance with the[RFC3986](http://tools.ietf.org/html/rfc3986) rules, which is the same as that for other parameter values. Take the DescribeInstances operation as an example. The request URL before a signature is:

    ```
    http://petadata.aliyuncs.com/?Timestamp=2013-06-01T10:33:56Z&Format=XML&Acce ssKeyId=testid&Action=DescribeInstances&SignatureMethod=HMAC-SHA1&Regi onId=region1&SignatureNonce=NwDAxvLU6tFE0DVb&Version=2014-08-15&Signatur eVersion=1.0
    ```

    The corresponding StringToSign is:

    ```
    GET&%2F&AccessKeyId%3Dtestid%26Action%DescribeInstances%26Format%3DXML %26RegionId%3Dregion1%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3DN wDAxvLU6tFE0DVb%26SignatureVersion%3D1.0%26Timestamp%3D2013-06-01T10%253 A33%253A56Z%26Version%3D2014-08-15 
    ```

    If the Accesskey ID used is "testid", Accesskey Secret is "testsecret", and the key used to calculate the HMAC is "testsecret &", the calculated signature is:

    ```
    GfQRtWbwdE8sp7q9lBgZyutVht8= 
    ```

    The signed request URL is \(with the Signature parameter added\):

    ```
    http://petadata.aliyuncs.com/?Timestamp=2012-12-26T10%3A33%3A56Z&Format=XML& AccessKeyId=testid&Action=DescribeInstances&SignatureMethod=HMAC-SHA1&RegionId=region1&SignatureNonce=NwDAxvLU6tFE0DVb&Version=2012-09-13&SignatureVersion=1.0&Signature= GfQRtWbwdE8sp7q9lBgZyutVht8%3d
    ```


