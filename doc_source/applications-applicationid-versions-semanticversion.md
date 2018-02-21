# Applications applicationId Versions semanticVersion<a name="applications-applicationid-versions-semanticversion"></a>

## URI<a name="applications-applicationid-versions-semanticversion-url"></a>

  / applications / *applicationId* / versions / *semanticVersion* 

## HTTP Methods<a name="applications-applicationid-versions-semanticversion-http-methods"></a>

### PUT<a name="applications-applicationid-versions-semanticversionput"></a>

Operation ID: CreateApplicationVersion 

Creates an application version\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
|  applicationId  | String | True |  The ID of the application to get\.  | 
|  semanticVersion  | String | True |  The semantic version of the new version\.  | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
|  201  |   [Version](#applications-applicationid-versions-semanticversion-response-body-version-example)   |  Success  | 
|  400  |   [BadRequestException](#applications-applicationid-versions-semanticversion-response-body-badrequestexception-example)   |  One of the parameters in the request is invalid\.  | 
|  500  |   [InternalServerErrorException](#applications-applicationid-versions-semanticversion-response-body-internalservererrorexception-example)   |  The AWS Serverless Application Repository service encountered an internal error\.  | 
|  403  |   [ForbiddenException](#applications-applicationid-versions-semanticversion-response-body-forbiddenexception-example)   |  The client is not authenticated\.  | 
|  429  |   [TooManyRequestsException](#applications-applicationid-versions-semanticversion-response-body-toomanyrequestsexception-example)   |  The client is sending more than the allowed number of requests per unit of time\.  | 
|  409  |   [ConflictException](#applications-applicationid-versions-semanticversion-response-body-conflictexception-example)   |  The resource already exists\.  | 

## Schemas<a name="applications-applicationid-versions-semanticversion-schemas"></a>

### Request Bodies<a name="applications-applicationid-versions-semanticversion-request-examples"></a>

#### Example PUT<a name="applications-applicationid-versions-semanticversion-request-body-put-example"></a>

```
{
  "[templateBody](#applications-applicationid-versions-semanticversion-createapplicationversioninput-templatebody)": "string",
  "[templateUrl](#applications-applicationid-versions-semanticversion-createapplicationversioninput-templateurl)": "string",
  "[sourceCodeUrl](#applications-applicationid-versions-semanticversion-createapplicationversioninput-sourcecodeurl)": "string"
}
```

### Response Bodies<a name="applications-applicationid-versions-semanticversion-response-examples"></a>

#### Example Version<a name="applications-applicationid-versions-semanticversion-response-body-version-example"></a>

```
{
  "[applicationId](#applications-applicationid-versions-semanticversion-version-applicationid)": "string",
  "[semanticVersion](#applications-applicationid-versions-semanticversion-version-semanticversion)": "string",
  "[sourceCodeUrl](#applications-applicationid-versions-semanticversion-version-sourcecodeurl)": "string",
  "[templateUrl](#applications-applicationid-versions-semanticversion-version-templateurl)": "string",
  "[creationTime](#applications-applicationid-versions-semanticversion-version-creationtime)": "string",
  "[parameterDefinitions](#applications-applicationid-versions-semanticversion-version-parameterdefinitions)": [
    {
      "[name](#applications-applicationid-versions-semanticversion-parameterdefinition-name)": "string",
      "[defaultValue](#applications-applicationid-versions-semanticversion-parameterdefinition-defaultvalue)": "string",
      "[description](#applications-applicationid-versions-semanticversion-parameterdefinition-description)": "string",
      "[type](#applications-applicationid-versions-semanticversion-parameterdefinition-type)": "string",
      "[noEcho](#applications-applicationid-versions-semanticversion-parameterdefinition-noecho)": boolean,
      "[allowedPattern](#applications-applicationid-versions-semanticversion-parameterdefinition-allowedpattern)": "string",
      "[constraintDescription](#applications-applicationid-versions-semanticversion-parameterdefinition-constraintdescription)": "string",
      "[minValue](#applications-applicationid-versions-semanticversion-parameterdefinition-minvalue)": integer,
      "[maxValue](#applications-applicationid-versions-semanticversion-parameterdefinition-maxvalue)": integer,
      "[minLength](#applications-applicationid-versions-semanticversion-parameterdefinition-minlength)": integer,
      "[maxLength](#applications-applicationid-versions-semanticversion-parameterdefinition-maxlength)": integer,
      "[allowedValues](#applications-applicationid-versions-semanticversion-parameterdefinition-allowedvalues)": [
        "string"
      ],
      "[referencedByResources](#applications-applicationid-versions-semanticversion-parameterdefinition-referencedbyresources)": [
        "string"
      ]
    }
  ]
}
```

#### Example BadRequestException<a name="applications-applicationid-versions-semanticversion-response-body-badrequestexception-example"></a>

```
{
  "[message](#applications-applicationid-versions-semanticversion-badrequestexception-message)": "string",
  "[errorCode](#applications-applicationid-versions-semanticversion-badrequestexception-errorcode)": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-versions-semanticversion-response-body-forbiddenexception-example"></a>

```
{
  "[message](#applications-applicationid-versions-semanticversion-forbiddenexception-message)": "string",
  "[errorCode](#applications-applicationid-versions-semanticversion-forbiddenexception-errorcode)": "string"
}
```

#### Example ConflictException<a name="applications-applicationid-versions-semanticversion-response-body-conflictexception-example"></a>

```
{
  "[message](#applications-applicationid-versions-semanticversion-conflictexception-message)": "string",
  "[errorCode](#applications-applicationid-versions-semanticversion-conflictexception-errorcode)": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-versions-semanticversion-response-body-toomanyrequestsexception-example"></a>

```
{
  "[message](#applications-applicationid-versions-semanticversion-toomanyrequestsexception-message)": "string",
  "[errorCode](#applications-applicationid-versions-semanticversion-toomanyrequestsexception-errorcode)": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-versions-semanticversion-response-body-internalservererrorexception-example"></a>

```
{
  "[message](#applications-applicationid-versions-semanticversion-internalservererrorexception-message)": "string",
  "[errorCode](#applications-applicationid-versions-semanticversion-internalservererrorexception-errorcode)": "string"
}
```

## Properties<a name="applications-applicationid-versions-semanticversion-properties"></a>


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


**CreateApplicationVersionInput**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   templateBody  |  string  | False |  The raw packaged AWS SAM template of your application\.  | 
|   templateUrl  |  string  | False |  A link to the packaged AWS SAM template of your application\.  | 
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


**ParameterDefinition**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
|   name  |  string  | True |  The name of the parameter\.  | 
|   defaultValue  |  string  | False |  A value of the appropriate type for the template to use if no value is specified when a stack is created\. If you define constraints for the parameter, you must specify a value that adheres to those constraints\.  | 
|   description  |  string  | False |  A string of up to 4,000 characters that describes the parameter\.  | 
|   type  |  string  | False |  The type of the parameter\. Valid values: `String | Number | List<Number> | CommaDelimitedList`   `String`: A literal string\. For example, users can specify `"MyUserName"`\.  `Number`: An integer or float\. AWS CloudFormation validates the parameter value as a number\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a string\. For example, users might specify `"8888"`\.  `List<Number>`: An array of integers or floats that are separated by commas\. AWS CloudFormation validates the parameter value as numbers\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a list of strings\. For example, users might specify "80,20", and then `Ref` results in `["80","20"]`\.  `CommaDelimitedList`: An array of literal strings that are separated by commas\. The total number of strings should be one more than the total number of commas\. Also, each member string is space\-trimmed\. For example, users might specify "test,dev,prod", and then `Ref` results in `["test","dev","prod"]`\.  | 
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
|   parameterDefinitions  |  Array of type  [ParameterDefinition](#applications-applicationid-versions-semanticversion-parameterdefinition)    | True |  An array of parameter types supported by the application\.  | 