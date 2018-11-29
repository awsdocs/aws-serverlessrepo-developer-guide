# Applications applicationId Dependencies<a name="applications-applicationid-dependencies"></a>

## URI<a name="applications-applicationid-dependencies-url"></a>

 /applications/ *applicationId* /dependencies 

## HTTP Methods<a name="applications-applicationid-dependencies-http-methods"></a>

### GET<a name="applications-applicationid-dependenciesget"></a>

Operation ID: ListApplicationDependencies 

Retrieves the list of applications nested in the containing application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  nextToken  | String | False |  A token to specify where to start paginating\.  | 
|  maxItems  | String | False |  The total number of items to return\.  | 
|  semanticVersion  | String | False |  The semantic version of the application to get\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationDependencyPage](#applications-applicationid-dependencies-response-body-applicationdependencypage-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-dependencies-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-dependencies-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-dependencies-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-dependencies-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-dependencies-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/ListApplicationDependencies) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/ListApplicationDependencies) 

## Schemas<a name="applications-applicationid-dependencies-schemas"></a>

### Response Bodies<a name="applications-applicationid-dependencies-response-examples"></a>

#### Example ApplicationDependencyPage<a name="applications-applicationid-dependencies-response-body-applicationdependencypage-example"></a>

```
{
  "dependencies": [
    {
      "applicationId": "string",
      "semanticVersion": "string"
    }
  ],
  "nextToken": "string"
}
```

#### Example BadRequestException<a name="applications-applicationid-dependencies-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-dependencies-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-dependencies-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-dependencies-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-dependencies-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-dependencies-properties"></a>


**ApplicationDependencyPage**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   dependencies  |  Array of type  [ApplicationDependencySummary](#applications-applicationid-dependencies-model-applicationdependencysummary)    | True |  An array of application summaries nested in the application\.  | 
|   nextToken  |  string  | False |  The token to request the next page of results\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ApplicationDependencyPage) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ApplicationDependencyPage) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ApplicationDependencyPage) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ApplicationDependencyPage) 


**ApplicationDependencySummary**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applicationId  |  string  | True |  The Amazon Resource Name \(ARN\) of the nested application\.  | 
|   semanticVersion  |  string  | True |  The semantic version of the nested application\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ApplicationDependencySummary) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ApplicationDependencySummary) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ApplicationDependencySummary) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ApplicationDependencySummary) 


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