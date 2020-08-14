# Applications applicationId Templates templateId<a name="applications-applicationid-templates-templateid"></a>

## URI<a name="applications-applicationid-templates-templateid-url"></a>

/applications/*applicationId*/templates/*templateId*

## HTTP Methods<a name="applications-applicationid-templates-templateid-http-methods"></a>

### GET<a name="applications-applicationid-templates-templateidget"></a>

Operation ID: GetCloudFormationTemplate

Gets the specified AWS CloudFormation template\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 
| templateId | String | True | The UUID returned by CreateCloudFormationTemplate\.Pattern: \[0\-9a\-fA\-F\]\{8\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{12\} | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

## Schemas<a name="applications-applicationid-templates-templateid-schemas"></a>

### Response Bodies<a name="applications-applicationid-templates-templateid-response-examples"></a>

#### Example TemplateDetails<a name="applications-applicationid-templates-templateid-response-body-templatedetails-example"></a>

```
{
  "templateId": "string",
  "templateUrl": "string",
  "applicationId": "string",
  "semanticVersion": "string",
  "status": enum,
  "creationTime": "string",
  "expirationTime": "string"
}
```

#### Example BadRequestException<a name="applications-applicationid-templates-templateid-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-templates-templateid-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-templates-templateid-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-templates-templateid-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-templates-templateid-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-templates-templateid-properties"></a>

### BadRequestException<a name="applications-applicationid-templates-templateid-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### ForbiddenException<a name="applications-applicationid-templates-templateid-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-templates-templateid-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-templates-templateid-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### TemplateDetails<a name="applications-applicationid-templates-templateid-model-templatedetails"></a>

Details of the template\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| templateId | string | True | The UUID returned by CreateCloudFormationTemplate\.Pattern: \[0\-9a\-fA\-F\]\{8\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{12\} | 
| templateUrl | string | True | A link to the template that can be used to deploy the application using AWS CloudFormation\. | 
| applicationId | string | True | The application Amazon Resource Name \(ARN\)\. | 
| semanticVersion | string | True | The semantic version of the application: [https://semver\.org/](https://semver.org/)  | 
| status | stringValues: `PREPARING \| ACTIVE \| EXPIRED` | True | Status of the template creation workflow\.Possible values: `PREPARING \| ACTIVE \| EXPIRED`  | 
| creationTime | string | True | The date and time this resource was created\. | 
| expirationTime | string | True | The date and time this template expires\. Templates expire 1 hour after creation\. | 

### TooManyRequestsException<a name="applications-applicationid-templates-templateid-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

## See Also<a name="applications-applicationid-templates-templateid-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### GetCloudFormationTemplate<a name="GetCloudFormationTemplate-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/GetCloudFormationTemplate)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/GetCloudFormationTemplate)