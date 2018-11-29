# Applications applicationId Policy<a name="applications-applicationid-policy"></a>

## URI<a name="applications-applicationid-policy-url"></a>

 /applications/ *applicationId* /policy 

## HTTP Methods<a name="applications-applicationid-policy-http-methods"></a>

### GET<a name="applications-applicationid-policyget"></a>

Operation ID: GetApplicationPolicy 

Retrieves the policy for the application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationPolicy](#applications-applicationid-policy-response-body-applicationpolicy-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-policy-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-policy-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-policy-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-policy-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-policy-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/GetApplicationPolicy) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/GetApplicationPolicy) 

### PUT<a name="applications-applicationid-policyput"></a>

Operation ID: PutApplicationPolicy 

Sets the permission policy for an application\. For the list of actions supported for this operation, see [Application Permissions](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/access-control-resource-based.html#application-permissions) \.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationPolicy](#applications-applicationid-policy-response-body-applicationpolicy-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-policy-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-policy-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-policy-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-policy-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-policy-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/PutApplicationPolicy) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/PutApplicationPolicy) 

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


**ApplicationPolicy**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   statements  |  Array of type  [ApplicationPolicyStatement](#applications-applicationid-policy-model-applicationpolicystatement)    | True |  An array of policy statements applied to the application\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ApplicationPolicy) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ApplicationPolicy) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ApplicationPolicy) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ApplicationPolicy) 


**ApplicationPolicyStatement**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   statementId  |  string  | False |  A unique ID for the statement\.  | 
|   principals  |  Array of type string   | True |  An AWS account ID, or \* to make the application public\.  | 
|   actions  |  Array of type string   | True |  For the list of actions supported for this operation, see [Application Permissions](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/access-control-resource-based.html#application-permissions)\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ApplicationPolicyStatement) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ApplicationPolicyStatement) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ApplicationPolicyStatement) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ApplicationPolicyStatement) 


**BadRequestException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  One of the parameters in the request is invalid\.  | 
|   errorCode  |  string  | False |  400  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/BadRequestException) 


**ForbiddenException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is not authenticated\.  | 
|   errorCode  |  string  | False |  403  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ForbiddenException) 


**InternalServerErrorException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|   errorCode  |  string  | False |  500  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/InternalServerErrorException) 


**NotFoundException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|   errorCode  |  string  | False |  404  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/NotFoundException) 


**TooManyRequestsException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is sending more than the allowed number of requests per unit of time\.  | 
|   errorCode  |  string  | False |  429  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/TooManyRequestsException) 