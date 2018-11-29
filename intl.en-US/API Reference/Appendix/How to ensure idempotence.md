# How to ensure idempotence {#concept_znz_vbp_mfb .concept}

If a request times out or an internal server error occurs when the CreateInstance operation is called, you may resend the request. In this case, you can prevent the server from creating redundant instances and ensure idempotence by specifying the ClientToken parameter, which is optional for the operation. A ClientToken is a user-defined, unique, and case-sensitive string, which is no more than 64 ASCII characters in length.

If you use the same ClientToken in multiple CreateInstance requests, the server considers these requests as the same request and returns the same results, including the InstanceId. Therefore, if an error occurs while creating an instance, you can send the request again by specifying the same ClientToken.

If the ClientToken does not match other parameters for the same instance being created, an IdempotentParameterMismatch error is returned. However, to prevent replay attacks, you must specify a different value for the SignatureNonce and Timestamp parameters for each request. Different values for SignatureNonce and Timestamp parameters lead to a change in the Signature value.

Typically, clients need to retry a request if a 500 \(InternetError\) or 503 \(ServiceUnavailable\) error is returned, or no response is received. If the last request is successful, retrying the request returns the same results, but will not cause the server to repeat the request.

