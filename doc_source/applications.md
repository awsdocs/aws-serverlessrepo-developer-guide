# Applications<a name="applications"></a>

## URI<a name="applications-url"></a>

 /applications 

## HTTP Methods<a name="applications-http-methods"></a>

### GET<a name="applicationsget"></a>

Operation ID: ListApplications 

Lists applications owned by the requester\.


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  maxItems  | String | False |  The total number of items to return\.  | 
|  nextToken  | String | False |  A token to specify where to start paginating\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  200  |   [ApplicationPage](#applications-response-body-applicationpage-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  404  |   [NotFoundException](#applications-response-body-notfoundexception-example)   |  The resource \(for example, an access policy statement\) specified in the request doesn't exist\.  | 

### POST<a name="applicationspost"></a>

Operation ID: CreateApplication 

Creates an application, optionally including an AWS SAM file to create the first application version in the same call\.


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  201  |   [Application](#applications-response-body-application-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  429  |   [TooManyRequestsException](#applications-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  409  |   [ConflictException](#applications-response-body-conflictexception-example)   |  The resource already exists\.  | 

## Schemas<a name="applications-schemas"></a>

### Request Bodies<a name="applications-request-examples"></a>

#### Example POST<a name="applications-request-body-post-example"></a>

```
{
  "name": "string",
  "description": "string",
  "author": "string",
  "spdxLicenseId": "string",
  "licenseBody": "string",
  "licenseUrl": "string",
  "readmeBody": "string",
  "readmeUrl": "string",
  "labels": [
    "string"
  ],
  "homePageUrl": "string",
  "semanticVersion": "string",
  "templateBody": "string",
  "templateUrl": "string",
  "sourceCodeUrl": "string"
}
```

### Response Bodies<a name="applications-response-examples"></a>

#### Example ApplicationPage<a name="applications-response-body-applicationpage-example"></a>

```
{
  "applications": [
    {
      "applicationId": "string",
      "name": "string",
      "description": "string",
      "author": "string",
      "spdxLicenseId": "string",
      "labels": [
        "string"
      ],
      "creationTime": "string",
      "homePageUrl": "string"
    }
  ],
  "nextToken": "string"
}
```

#### Example Application<a name="applications-response-body-application-example"></a>

```
{
  "applicationId": "string",
  "name": "string",
  "description": "string",
  "author": "string",
  "spdxLicenseId": "string",
  "licenseUrl": "string",
  "readmeUrl": "string",
  "labels": [
    "string"
  ],
  "creationTime": "string",
  "homePageUrl": "string",
  "version": {
    "applicationId": "string",
    "semanticVersion": "string",
    "sourceCodeUrl": "string",
    "templateUrl": "string",
    "creationTime": "string",
    "parameterDefinitions": [
      {
        "name": "string",
        "defaultValue": "string",
        "description": "string",
        "type": "string",
        "noEcho": boolean,
        "allowedPattern": "string",
        "constraintDescription": "string",
        "minValue": integer,
        "maxValue": integer,
        "minLength": integer,
        "maxLength": integer,
        "allowedValues": [
          "string"
        ],
        "referencedByResources": [
          "string"
        ]
      }
    ]
  }
}
```

#### Example BadRequestException<a name="applications-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ConflictException<a name="applications-response-body-conflictexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-properties"></a>


**Application**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applicationId  |  string  | True |  The application Amazon Resource Name \(ARN\)\.  | 
|   name  |  string  | True |  The name of the application\. Minimum length=1\. Maximum length=140 Pattern: "\[a\-zA\-Z0\-9\\\\\-\]\+";  | 
|   description  |  string  | True |  The description of the application\. Minimum length=1\. Maximum length=256  | 
|   author  |  string  | True |  The name of the author publishing the app\. Minimum length=1\. Maximum length=127\. Pattern "^\[a\-z0\-9\]\(\(\[a\-z0\-9\]\|\-\(?\!\-\)\)\*\[a\-z0\-9\]\)?$";  | 
|   spdxLicenseId  |  string  | False |  A valid identifier from https://spdx\.org/licenses/\.  | 
|   licenseUrl  |  string  | False |  A link to a license file of the app that matches the spdxLicenseID value of your application\. Maximum size 5 MB  | 
|   readmeUrl  |  string  | False |  A link to the readme file in Markdown language that contains a more detailed description of the application and how it works\. Maximum size 5 MB  | 
|   labels  |  Array of type string   | False |  Labels to improve discovery of apps in search results\. Minimum length=1\. Maximum length=127\. Maximum number of labels: 10 Pattern: "^\[a\-zA\-Z0\-9\+\\\\\-\_:\\\\/@\]\+$";  | 
|   creationTime  |  string  | False |  The date and time this resource was created\.  | 
|   homePageUrl  |  string  | False |  A URL with more information about the application, for example the location of your GitHub repository for the application\.  | 
|   version  |   [Version](#applications-version)   | False |  Version information about the application\.  | 


**ApplicationPage**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applications  |  Array of type  [ApplicationSummary](#applications-applicationsummary)    | True |  An array of application summaries\.  | 
|   nextToken  |  string  | False |  The token to request the next page of results\.  | 


**ApplicationSummary**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applicationId  |  string  | True |  The application Amazon Resource Name \(ARN\)\.  | 
|   name  |  string  | True |  The name of the application\. Minimum length=1\. Maximum length=140 Pattern: "\[a\-zA\-Z0\-9\\\\\-\]\+";  | 
|   description  |  string  | True |  The description of the application\. Minimum length=1\. Maximum length=256  | 
|   author  |  string  | True |  The name of the author publishing the app\. Minimum length=1\. Maximum length=127\. Pattern "^\[a\-z0\-9\]\(\(\[a\-z0\-9\]\|\-\(?\!\-\)\)\*\[a\-z0\-9\]\)?$";  | 
|   spdxLicenseId  |  string  | False |  A valid identifier from [https://spdx\.org/licenses/](https://spdx.org/licenses/)\.  | 
|   labels  |  Array of type string   | False |  Labels to improve discovery of apps in search results\. Minimum length=1\. Maximum length=127\. Maximum number of labels: 10 Pattern: "^\[a\-zA\-Z0\-9\+\\\\\-\_:\\\\/@\]\+$";  | 
|   creationTime  |  string  | False |  The date and time this resource was created\.  | 
|   homePageUrl  |  string  | False |  A URL with more information about the application, for example the location of your GitHub repository for the application\.  | 


**BadRequestException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  One of the parameters in the request is invalid\.  | 
|   errorCode  |  string  | False |  400  | 


**ConflictException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The resource already exists\.  | 
|   errorCode  |  string  | False |  409  | 


**CreateApplicationInput**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   name  |  string  | True |  The name of the application that you want to publish\. Minimum length=1\. Maximum length=140 Pattern: "\[a\-zA\-Z0\-9\\\\\-\]\+";  | 
|   description  |  string  | True |  The description of the application\. Minimum length=1\. Maximum length=256  | 
|   author  |  string  | True |  The name of the author publishing the app\. Minimum length=1\. Maximum length=127\. Pattern "^\[a\-z0\-9\]\(\(\[a\-z0\-9\]\|\-\(?\!\-\)\)\*\[a\-z0\-9\]\)?$";  | 
|   spdxLicenseId  |  string  | False |  A valid identifier from [https://spdx\.org/licenses/](https://spdx.org/licenses/)\.  | 
|   licenseBody  |  string  | False |  A local text file that contains the license of the app that matches the spdxLicenseID value of your application\. The file has the format `file://<path>/<filename>`\. Maximum size 5 MB You can specify only one of `licenseBody` and `licenseUrl`; otherwise, an error results\.  | 
|   licenseUrl  |  string  | False |  A link to the S3 object that contains the license of the app that matches the spdxLicenseID value of your application\. Maximum size 5 MB You can specify only one of `licenseBody` and `licenseUrl`; otherwise, an error results\.  | 
|   readmeBody  |  string  | False |  A local text readme file in Markdown language that contains a more detailed description of the application and how it works\. The file has the format `file://<path>/<filename>`\. Maximum size 5 MB You can specify only one of `readmeBody` and `readmeUrl`; otherwise, an error results\.  | 
|   readmeUrl  |  string  | False |  A link to the S3 object in Markdown language that contains a more detailed description of the application and how it works\. Maximum size 5 MB You can specify only one of `readmeBody` and `readmeUrl`; otherwise, an error results\.  | 
|   labels  |  Array of type string   | False |  Labels to improve discovery of apps in search results\. Minimum length=1\. Maximum length=127\. Maximum number of labels: 10 Pattern: "^\[a\-zA\-Z0\-9\+\\\\\-\_:\\\\/@\]\+$";  | 
|   homePageUrl  |  string  | False |  A URL with more information about the application, for example the location of your GitHub repository for the application\.  | 
|   semanticVersion  |  string  | False |  The semantic version of the application:  [https://semver\.org/](https://semver.org/)   | 
|   templateBody  |  string  | False |  The local raw packaged AWS SAM template file of your application\. The file has the format `file://<path>/<filename>`\. You can specify only one of `templateBody` and `templateUrl`; otherwise an error results\.  | 
|   templateUrl  |  string  | False |  A link to the S3 object containing the packaged AWS SAM template of your application\. You can specify only one of `templateBody` and `templateUrl`; otherwise an error results\.  | 
|   sourceCodeUrl  |  string  | False |  A link to a public repository for the source code of your application\.  | 


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


**ParameterDefinition**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   name  |  string  | True |  The name of the parameter\.  | 
|   defaultValue  |  string  | False |  A value of the appropriate type for the template to use if no value is specified when a stack is created\. If you define constraints for the parameter, you must specify a value that adheres to those constraints\.  | 
|   description  |  string  | False |  A string of up to 4,000 characters that describes the parameter\.  | 
|   type  |  string  | False |  The type of the parameter\. Valid values: `String \| Number \| List<Number> \| CommaDelimitedList`   `String`: A literal string\. For example, users can specify `"MyUserName"`\.  `Number`: An integer or float\. AWS CloudFormation validates the parameter value as a number\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a string\. For example, users might specify `"8888"`\.  `List<Number>`: An array of integers or floats that are separated by commas\. AWS CloudFormation validates the parameter value as numbers\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a list of strings\. For example, users might specify "80,20", and then `Ref` results in `["80","20"]`\.  `CommaDelimitedList`: An array of literal strings that are separated by commas\. The total number of strings should be one more than the total number of commas\. Also, each member string is space\-trimmed\. For example, users might specify "test,dev,prod", and then `Ref` results in `["test","dev","prod"]`\.  | 
|   noEcho  |  boolean  | False |  Whether to mask the parameter value whenever anyone makes a call that describes the stack\. If you set the value to true, the parameter value is masked with asterisks \(\*\*\*\*\*\)\.  | 
|   allowedPattern  |  string  | False |  A regular expression that represents the patterns to allow for `String` types\.  | 
|   constraintDescription  |  string  | False |  A string that explains a constraint when the constraint is violated\. For example, without a constraint description, a parameter that has an allowed pattern of `[A-Za-z0-9]+` displays the following error message when the user specifies an invalid value:  `Malformed input-Parameter MyParameter must match pattern [A-Za-z0-9]+`  By adding a constraint description, such as "must contain only uppercase and lowercase letters and numbers," you can display the following customized error message:  `Malformed input-Parameter MyParameter must contain only uppercase and lowercase letters and numbers.`   | 
|   minValue  |  integer  | False |  A numeric value that determines the smallest numeric value that you want to allow for `Number` types\.  | 
|   maxValue  |  integer  | False |  A numeric value that determines the largest numeric value that you want to allow for `Number` types\.  | 
|   minLength  |  integer  | False |  An integer value that determines the smallest number of characters that you want to allow for `String` types\.  | 
|   maxLength  |  integer  | False |  An integer value that determines the largest number of characters that you want to allow for `String` types\.  | 
|   allowedValues  |  Array of type string   | False |  An array containing the list of values allowed for the parameter\.  | 
|   referencedByResources  |  Array of type string   | True |  A list of AWS SAM resources that use this parameter\.  | 


**TooManyRequestsException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   message  |  string  | False |  The client is sending more than the allowed number of requests per unit of time\.  | 
|   errorCode  |  string  | False |  429  | 


**Version**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   applicationId  |  string  | True |  The application Amazon Resource Name \(ARN\)\.  | 
|   semanticVersion  |  string  | True |  The semantic version of the application:  [https://semver\.org/](https://semver.org/)   | 
|   sourceCodeUrl  |  string  | False |  A link to a public repository for the source code of your application\.  | 
|   templateUrl  |  string  | True |  A link to the packaged AWS SAM template of your application\.  | 
|   creationTime  |  string  | True |  The date and time this resource was created\.  | 
|   parameterDefinitions  |  Array of type  [ParameterDefinition](#applications-parameterdefinition)    | True |  An array of parameter types supported by the application\.  | 