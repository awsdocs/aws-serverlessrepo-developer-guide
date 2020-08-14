# Applications applicationId Unshare<a name="applications-applicationid-unshare"></a>

## URI<a name="applications-applicationid-unshare-url"></a>

/applications/*applicationId*/unshare

## HTTP Methods<a name="applications-applicationid-unshare-http-methods"></a>

### POST<a name="applications-applicationid-unsharepost"></a>

Operation ID: UnshareApplication

Unshares an application from an AWS Organization\.

This operation can be called only from the organization's master account\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 204 | None | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

## Schemas<a name="applications-applicationid-unshare-schemas"></a>

### Request Bodies<a name="applications-applicationid-unshare-request-examples"></a>

#### Example POST<a name="applications-applicationid-unshare-request-body-post-example"></a>

```
{
  "organizationId": "string"
}
```

### Response Bodies<a name="applications-applicationid-unshare-response-examples"></a>

#### Example BadRequestException<a name="applications-applicationid-unshare-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-unshare-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-unshare-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-unshare-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-unshare-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-unshare-properties"></a>

### BadRequestException<a name="applications-applicationid-unshare-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### ForbiddenException<a name="applications-applicationid-unshare-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-unshare-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-unshare-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### TooManyRequestsException<a name="applications-applicationid-unshare-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

### UnshareApplicationInput<a name="applications-applicationid-unshare-model-unshareapplicationinput"></a>

Unshare application request\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| organizationId | string | True | The AWS Organization ID to unshare the application from\. | 

## See Also<a name="applications-applicationid-unshare-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### UnshareApplication<a name="UnshareApplication-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/UnshareApplication)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/UnshareApplication)