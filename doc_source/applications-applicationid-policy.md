# Applications applicationId Policy<a name="applications-applicationid-policy"></a>

## URI<a name="applications-applicationid-policy-url"></a>

 /applications/ *applicationId* /policy 

## HTTP Methods<a name="applications-applicationid-policy-http-methods"></a>

### GET<a name="applications-applicationid-policyget"></a>

Operation ID: GetApplicationPolicy 

Gets the policy for the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The ID of the application to get\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationPolicy](#applications-applicationid-policy-response-body-applicationpolicy-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-policy-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-policy-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-policy-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-policy-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-policy-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 

### PUT<a name="applications-applicationid-policyput"></a>

Operation ID: PutApplicationPolicy 

Puts the policy for the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The ID of the application to get\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationPolicy](#applications-applicationid-policy-response-body-applicationpolicy-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-policy-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-policy-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-policy-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-applicationid-policy-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-policy-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 

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
|   statements  |  Array of type  [ApplicationPolicyStatement](#applications-applicationid-policy-applicationpolicystatement)    | True |  An array of policy statements applied to the application\.  | 


**ApplicationPolicyStatement**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   statementId  |  string  | False |  A unique ID for the statement\.  | 
|   principals  |  Array of type string   | True |  An AWS account ID, or \* to make the application public\.  | 
|   actions  |  Array of type string   | True |  A list of supported actions:  `GetApplication`   `CreateCloudFormationChangeSet`   `ListApplicationVersions`   `SearchApplications`   `Deploy` \(Note: This action enables all other actions preceding\.\)  | 


**BadRequestException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  One of the parameters in the request is invalid\.  | 
|   errorCode  |  string  | False |  400  | 


**ForbiddenException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is not authenticated\.  | 
|   errorCode  |  string  | False |  403  | 


**InternalServerErrorException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|   errorCode  |  string  | False |  500  | 


**NotFoundException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 
|   errorCode  |  string  | False |  404  | 


**TooManyRequestsException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is sending more than the allowed number of requests per unit of time\.  | 
|   errorCode  |  string  | False |  429  | 