# Applications applicationId Versions<a name="applications-applicationid-versions"></a>

## URI<a name="applications-applicationid-versions-url"></a>

/applications/*applicationId*/versions

## HTTP Methods<a name="applications-applicationid-versions-http-methods"></a>

### GET<a name="applications-applicationid-versionsget"></a>

Operation ID: ListApplicationVersions

Lists versions for the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| maxItems | String | False | The total number of items to return\. | 
| nextToken | String | False | A token to specify where to start paginating\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

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

### ApplicationVersionPage<a name="applications-applicationid-versions-model-applicationversionpage"></a>

A list of version summaries for the application\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| versions | Array of type [VersionSummary](#applications-applicationid-versions-model-versionsummary) | True | An array of version summaries for the application\. | 
| nextToken | string | False | The token to request the next page of results\. | 

### BadRequestException<a name="applications-applicationid-versions-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### ForbiddenException<a name="applications-applicationid-versions-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-versions-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-versions-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### TooManyRequestsException<a name="applications-applicationid-versions-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

### VersionSummary<a name="applications-applicationid-versions-model-versionsummary"></a>

An application version summary\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | string | True | The application Amazon Resource Name \(ARN\)\. | 
| semanticVersion | string | True | The semantic version of the application: [https://semver\.org/](https://semver.org/)  | 
| sourceCodeUrl | string | False | A link to a public repository for the source code of your application, for example the URL of a specific GitHub commit\. | 
| creationTime | string | True | The date and time this resource was created\. | 

## See Also<a name="applications-applicationid-versions-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### ListApplicationVersions<a name="ListApplicationVersions-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/ListApplicationVersions)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/ListApplicationVersions)