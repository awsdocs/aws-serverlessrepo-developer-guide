# Applications applicationId Dependencies<a name="applications-applicationid-dependencies"></a>

## URI<a name="applications-applicationid-dependencies-url"></a>

/applications/*applicationId*/dependencies

## HTTP Methods<a name="applications-applicationid-dependencies-http-methods"></a>

### GET<a name="applications-applicationid-dependenciesget"></a>

Operation ID: ListApplicationDependencies

Retrieves the list of applications nested in the containing application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| nextToken | String | False | A token to specify where to start paginating\. | 
| maxItems | String | False | The total number of items to return\. | 
| semanticVersion | String | False | The semantic version of the application to get\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

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

### ApplicationDependencyPage<a name="applications-applicationid-dependencies-model-applicationdependencypage"></a>

A list of application summaries nested in the application\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| dependencies | Array of type [ApplicationDependencySummary](#applications-applicationid-dependencies-model-applicationdependencysummary) | True | An array of application summaries nested in the application\. | 
| nextToken | string | False | The token to request the next page of results\. | 

### ApplicationDependencySummary<a name="applications-applicationid-dependencies-model-applicationdependencysummary"></a>

A nested application summary\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | string | True | The Amazon Resource Name \(ARN\) of the nested application\. | 
| semanticVersion | string | True | The semantic version of the nested application\. | 

### BadRequestException<a name="applications-applicationid-dependencies-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### ForbiddenException<a name="applications-applicationid-dependencies-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-dependencies-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-dependencies-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### TooManyRequestsException<a name="applications-applicationid-dependencies-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

## See Also<a name="applications-applicationid-dependencies-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### ListApplicationDependencies<a name="ListApplicationDependencies-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/ListApplicationDependencies)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/ListApplicationDependencies)