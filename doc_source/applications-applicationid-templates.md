# Applications applicationId Templates<a name="applications-applicationid-templates"></a>

## URI<a name="applications-applicationid-templates-url"></a>

 /applications/ *applicationId* /templates 

## HTTP Methods<a name="applications-applicationid-templates-http-methods"></a>

### POST<a name="applications-applicationid-templatespost"></a>

Operation ID: CreateCloudFormationTemplate 

Creates an AWS CloudFormation template\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  201  |   [TemplateDetails](#applications-applicationid-templates-response-body-templatedetails-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-templates-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-templates-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-templates-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-templates-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/CreateCloudFormationTemplate) 

## Schemas<a name="applications-applicationid-templates-schemas"></a>

### Request Bodies<a name="applications-applicationid-templates-request-examples"></a>

#### Example POST<a name="applications-applicationid-templates-request-body-post-example"></a>

```
{
  "semanticVersion": "string"
}
```

### Response Bodies<a name="applications-applicationid-templates-response-examples"></a>

#### Example TemplateDetails<a name="applications-applicationid-templates-response-body-templatedetails-example"></a>

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

#### Example BadRequestException<a name="applications-applicationid-templates-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-templates-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-templates-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-templates-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-templates-properties"></a>


**BadRequestException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  One of the parameters in the request is invalid\.  | 
|   errorCode  |  string  | False |  400  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/BadRequestException) 


**CreateCloudFormationTemplateInput**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   semanticVersion  |  string  | False |  The semantic version of the application:  [https://semver\.org/](https://semver.org/)   | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/CreateCloudFormationTemplateInput) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/CreateCloudFormationTemplateInput) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/CreateCloudFormationTemplateInput) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/CreateCloudFormationTemplateInput) 


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


**TemplateDetails**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   templateId  |  string  | True |  The UUID returned by CreateCloudFormationTemplate\. Pattern: \[0\-9a\-fA\-F\]\{8\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{12\}  | 
|   templateUrl  |  string  | True |  A link to the template that can be used to deploy the application using AWS CloudFormation\.  | 
|   applicationId  |  string  | True |  The application Amazon Resource Name \(ARN\)\.  | 
|   semanticVersion  |  string  | True |  The semantic version of the application:  [https://semver\.org/](https://semver.org/)   | 
|   status  |  string  Values: `PREPARING \| ACTIVE \| EXPIRED`   | True |  Status of the template creation workflow\. Possible values: `PREPARING \| ACTIVE \| EXPIRED`   | 
|   creationTime  |  string  | True |  The date and time this resource was created\.  | 
|   expirationTime  |  string  | True |  The date and time this template expires\. Templates expire 1 hour after creation\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/TemplateDetails) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/TemplateDetails) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/TemplateDetails) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/TemplateDetails) 


**TooManyRequestsException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is sending more than the allowed number of requests per unit of time\.  | 
|   errorCode  |  string  | False |  429  | 

 **See Also** 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/TooManyRequestsException) 