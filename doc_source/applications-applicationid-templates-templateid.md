# Applications applicationId Templates templateId<a name="applications-applicationid-templates-templateid"></a>

## URI<a name="applications-applicationid-templates-templateid-url"></a>

 /applications/ *applicationId* /templates/ *templateId* 

## HTTP Methods<a name="applications-applicationid-templates-templateid-http-methods"></a>

### GET<a name="applications-applicationid-templates-templateidget"></a>

Operation ID: GetCloudFormationTemplate 

Gets the specified AWS CloudFormation template\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 
|  templateId  | String | True |  The UUID returned by CreateCloudFormationTemplate\. Pattern: \[0\-9a\-fA\-F\]\{8\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{4\}\\\-\[0\-9a\-fA\-F\]\{12\}  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [TemplateDetails](#applications-applicationid-templates-templateid-response-body-templatedetails-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-templates-templateid-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-templates-templateid-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-templates-templateid-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-templates-templateid-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-templates-templateid-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/GetCloudFormationTemplate) 

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