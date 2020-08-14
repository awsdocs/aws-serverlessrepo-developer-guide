# Applications applicationId Policy<a name="applications-applicationid-policy"></a>

## URI<a name="applications-applicationid-policy-url"></a>

/applications/*applicationId*/policy

## HTTP Methods<a name="applications-applicationid-policy-http-methods"></a>

### GET<a name="applications-applicationid-policyget"></a>

Operation ID: GetApplicationPolicy

Retrieves the policy for the application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

### PUT<a name="applications-applicationid-policyput"></a>

Operation ID: PutApplicationPolicy

Sets the permission policy for an application\. For the list of actions supported for this operation, see [Application Permissions](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/access-control-resource-based.html#application-permissions) \.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

## Schemas<a name="applications-applicationid-policy-schemas"></a>

### Request Bodies<a name="applications-applicationid-policy-request-examples"></a>

#### Example PUT<a name="applications-applicationid-policy-request-body-put-example"></a>

```
{
  "statements": [
    {
      "statementId": "string",
      "principals": [
        "string"
      ],
      "actions": [
        "string"
      ],
      "principalOrgIDs": [
        "string"
      ]
    }
  ]
}
```

### Response Bodies<a name="applications-applicationid-policy-response-examples"></a>

#### Example ApplicationPolicy<a name="applications-applicationid-policy-response-body-applicationpolicy-example"></a>

```
{
  "statements": [
    {
      "statementId": "string",
      "principals": [
        "string"
      ],
      "actions": [
        "string"
      ],
      "principalOrgIDs": [
        "string"
      ]
    }
  ]
}
```

#### Example BadRequestException<a name="applications-applicationid-policy-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-policy-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-policy-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-policy-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-policy-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-policy-properties"></a>

### ApplicationPolicy<a name="applications-applicationid-policy-model-applicationpolicy"></a>

Policy statements applied to the application\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| statements | Array of type [ApplicationPolicyStatement](#applications-applicationid-policy-model-applicationpolicystatement) | True | An array of policy statements applied to the application\. | 

### ApplicationPolicyStatement<a name="applications-applicationid-policy-model-applicationpolicystatement"></a>

Policy statement applied to the application\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| statementId | string | False | A unique ID for the statement\. | 
| principals | Array of type string | True | An array of AWS account IDs to share the application with, or \* to make the application public\. | 
| actions | Array of type string | True | For the list of actions supported for this operation, see [Application Permissions](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/access-control-resource-based.html#application-permissions)\. | 
| principalOrgIDs | Array of type string | False | The AWS Organization ID to share the application with\. | 

### BadRequestException<a name="applications-applicationid-policy-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### ForbiddenException<a name="applications-applicationid-policy-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-policy-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-policy-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### TooManyRequestsException<a name="applications-applicationid-policy-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

## See Also<a name="applications-applicationid-policy-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### GetApplicationPolicy<a name="GetApplicationPolicy-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/GetApplicationPolicy)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/GetApplicationPolicy)

### PutApplicationPolicy<a name="PutApplicationPolicy-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/PutApplicationPolicy)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/PutApplicationPolicy)