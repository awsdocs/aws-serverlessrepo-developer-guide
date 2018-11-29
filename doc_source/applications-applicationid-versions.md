# Applications applicationId Versions<a name="applications-applicationid-versions"></a>

## URI<a name="applications-applicationid-versions-url"></a>

 /applications/ *applicationId* /versions 

## HTTP Methods<a name="applications-applicationid-versions-http-methods"></a>

### GET<a name="applications-applicationid-versionsget"></a>

Operation ID: ListApplicationVersions 

Lists versions for the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The Amazon Resource Name \(ARN\) of the application\.  | 


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  maxItems  | String | False |  The total number of items to return\.  | 
|  nextToken  | String | False |  A token to specify where to start paginating\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationVersionPage](#applications-applicationid-versions-response-body-applicationversionpage-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-versions-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-versions-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-versions-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-versions-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-versions-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 

 **See Also** 
+  [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/ListApplicationVersions) 
+  [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/ListApplicationVersions) 

## Schemas<a name="applications-applicationid-versions-schemas"></a>

### Response Bodies<a name="applications-applicationid-versions-response-examples"></a>

#### Example ApplicationVersionPage<a name="applications-applicationid-versions-response-body-applicationversionpage-example"></a>

```
{
  "versions": [
    {
      "applicationId": "string",
      "semanticVersion": "string",
      "sourceCodeUrl": "string",
      "creationTime": "string"
    }
  ],
  "nextToken": "string"
}
```

#### Example BadRequestException<a name="applications-applicationid-versions-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-versions-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-versions-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-versions-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-versions-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-versions-properties"></a>


**ApplicationVersionPage**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   versions  |  Array of type  [VersionSummary](#applications-applicationid-versions-model-versionsummary)    | True |  An array of version summaries for the application\.  | 
|   nextToken  |  string  | False |  The token to request the next page of results\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ApplicationVersionPage) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ApplicationVersionPage) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ApplicationVersionPage) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ApplicationVersionPage) 


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


**VersionSummary**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applicationId  |  string  | True |  The application Amazon Resource Name \(ARN\)\.  | 
|   semanticVersion  |  string  | True |  The semantic version of the application:  [https://semver\.org/](https://semver.org/)   | 
|   sourceCodeUrl  |  string  | False |  A link to a public repository for the source code of your application\.  | 
|   creationTime  |  string  | True |  The date and time this resource was created\.  | 

 **See Also** 
+  [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/VersionSummary) 
+  [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/VersionSummary) 
+  [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/VersionSummary) 
+  [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/VersionSummary) 