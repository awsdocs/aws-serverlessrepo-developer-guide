# Applications applicationId Versions semanticVersion<a name="applications-applicationid-versions-semanticversion"></a>

## URI<a name="applications-applicationid-versions-semanticversion-url"></a>

/applications/*applicationId*/versions/*semanticVersion*

## HTTP Methods<a name="applications-applicationid-versions-semanticversion-http-methods"></a>

### PUT<a name="applications-applicationid-versions-semanticversionput"></a>

Operation ID: CreateApplicationVersion

Creates an application version\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 
| semanticVersion | String | True | The semantic version of the new version\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 201 | [Version](#applications-applicationid-versions-semanticversion-response-body-version-example) | Success | 
| 400 | [BadRequestException](#applications-applicationid-versions-semanticversion-response-body-badrequestexception-example) | One of the parameters in the request is invalid\. | 
| 403 | [ForbiddenException](#applications-applicationid-versions-semanticversion-response-body-forbiddenexception-example) | The client is not authenticated\. | 
| 409 | [ConflictException](#applications-applicationid-versions-semanticversion-response-body-conflictexception-example) | The resource already exists\. | 
| 429 | [TooManyRequestsException](#applications-applicationid-versions-semanticversion-response-body-toomanyrequestsexception-example) | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 | [InternalServerErrorException](#applications-applicationid-versions-semanticversion-response-body-internalservererrorexception-example) | The AWS Serverless Application Repository service encountered an internal error\. | 

**See Also**
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for Go \- Pilot](/goto/SdkForGoPilot/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/CreateApplicationVersion)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/CreateApplicationVersion)

## Schemas<a name="applications-applicationid-versions-semanticversion-schemas"></a>

### Request Bodies<a name="applications-applicationid-versions-semanticversion-request-examples"></a>

#### Example PUT<a name="applications-applicationid-versions-semanticversion-request-body-put-example"></a>

```
{
  "templateBody": "string",
  "templateUrl": "string",
  "sourceCodeUrl": "string",
  "sourceCodeArchiveUrl": "string"
}
```

### Response Bodies<a name="applications-applicationid-versions-semanticversion-response-examples"></a>

#### Example Version<a name="applications-applicationid-versions-semanticversion-response-body-version-example"></a>

```
{
  "applicationId": "string",
  "semanticVersion": "string",
  "sourceCodeUrl": "string",
  "sourceCodeArchiveUrl": "string",
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
  ],
  "requiredCapabilities": [
    enum
  ],
  "resourcesSupported": boolean
}
```

#### Example BadRequestException<a name="applications-applicationid-versions-semanticversion-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-versions-semanticversion-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ConflictException<a name="applications-applicationid-versions-semanticversion-response-body-conflictexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-versions-semanticversion-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-versions-semanticversion-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-versions-semanticversion-properties"></a>


**BadRequestException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

**See Also**
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/BadRequestException)

**Capability \(enum\)**

Values that must be specified in order to deploy some applications\.
+ CAPABILITY\_IAM
+ CAPABILITY\_NAMED\_IAM
+ CAPABILITY\_AUTO\_EXPAND
+ CAPABILITY\_RESOURCE\_POLICY


**ConflictException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource already exists\. | 
| errorCode | string | False | 409 | 

**See Also**
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ConflictException)


**CreateApplicationVersionInput**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| templateBody | string | False | The raw packaged AWS SAM template of your application\. | 
| templateUrl | string | False | A link to the packaged AWS SAM template of your application\. | 
| sourceCodeUrl | string | False | A link to a public repository for the source code of your application, for example the URL of a specific GitHub commit\. | 
| sourceCodeArchiveUrl | string | False | A link to the S3 object that contains the ZIP archive of the source code for this version of your application\.Maximum size 50 MB | 

**See Also**
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/CreateApplicationVersionInput)
+ [AWS SDK for Go \- Pilot](/goto/SdkForGoPilot/serverlessrepo-2017-09-08/CreateApplicationVersionInput)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/CreateApplicationVersionInput)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/CreateApplicationVersionInput)
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/CreateApplicationVersionInput)


**ForbiddenException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

**See Also**
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ForbiddenException)


**InternalServerErrorException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

**See Also**
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/InternalServerErrorException)


**ParameterDefinition**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| name | string | True | The name of the parameter\. | 
| defaultValue | string | False | A value of the appropriate type for the template to use if no value is specified when a stack is created\. If you define constraints for the parameter, you must specify a value that adheres to those constraints\. | 
| description | string | False | A string of up to 4,000 characters that describes the parameter\. | 
| type | string | False | The type of the parameter\.Valid values: `String \| Number \| List<Number> \| CommaDelimitedList`  `String`: A literal string\.For example, users can specify `"MyUserName"`\. `Number`: An integer or float\. AWS CloudFormation validates the parameter value as a number\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a string\.For example, users might specify `"8888"`\. `List<Number>`: An array of integers or floats that are separated by commas\. AWS CloudFormation validates the parameter value as numbers\. However, when you use the parameter elsewhere in your template \(for example, by using the `Ref` intrinsic function\), the parameter value becomes a list of strings\.For example, users might specify "80,20", and then `Ref` results in `["80","20"]`\. `CommaDelimitedList`: An array of literal strings that are separated by commas\. The total number of strings should be one more than the total number of commas\. Also, each member string is space\-trimmed\.For example, users might specify "test,dev,prod", and then `Ref` results in `["test","dev","prod"]`\. | 
| noEcho | boolean | False | Whether to mask the parameter value whenever anyone makes a call that describes the stack\. If you set the value to true, the parameter value is masked with asterisks \(\*\*\*\*\*\)\. | 
| allowedPattern | string | False | A regular expression that represents the patterns to allow for `String` types\. | 
| constraintDescription | string | False | A string that explains a constraint when the constraint is violated\. For example, without a constraint description, a parameter that has an allowed pattern of `[A-Za-z0-9]+` displays the following error message when the user specifies an invalid value: `Malformed input-Parameter MyParameter must match pattern [A-Za-z0-9]+` By adding a constraint description, such as "must contain only uppercase and lowercase letters and numbers," you can display the following customized error message: `Malformed input-Parameter MyParameter must contain only uppercase and lowercase letters and numbers.`  | 
| minValue | integer | False | A numeric value that determines the smallest numeric value that you want to allow for `Number` types\. | 
| maxValue | integer | False | A numeric value that determines the largest numeric value that you want to allow for `Number` types\. | 
| minLength | integer | False | An integer value that determines the smallest number of characters that you want to allow for `String` types\. | 
| maxLength | integer | False | An integer value that determines the largest number of characters that you want to allow for `String` types\. | 
| allowedValues | array | False | An array containing the list of values allowed for the parameter\. | 
| referencedByResources | array | True | A list of AWS SAM resources that use this parameter\. | 

**See Also**
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/ParameterDefinition)
+ [AWS SDK for Go \- Pilot](/goto/SdkForGoPilot/serverlessrepo-2017-09-08/ParameterDefinition)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/ParameterDefinition)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/ParameterDefinition)
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/ParameterDefinition)


**TooManyRequestsException**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

**See Also**
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/TooManyRequestsException)


**Version**  

| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | string | True | The application Amazon Resource Name \(ARN\)\. | 
| semanticVersion | string | True | The semantic version of the application: [https://semver\.org/](https://semver.org/)  | 
| sourceCodeUrl | string | False | A link to a public repository for the source code of your application, for example the URL of a specific GitHub commit\. | 
| sourceCodeArchiveUrl | string | False | A link to the S3 object that contains the ZIP archive of the source code for this version of your application\.Maximum size 50 MB | 
| templateUrl | string | True | A link to the packaged AWS SAM template of your application\. | 
| creationTime | string | True | The date and time this resource was created\. | 
| parameterDefinitions | array | True | An array of parameter types supported by the application\. | 
| requiredCapabilities | array | True | A list of values that you must specify before you can deploy certain applications\. Some applications might include resources that can affect permissions in your AWS account, for example, by creating new AWS Identity and Access Management \(IAM\) users\. For those applications, you must explicitly acknowledge their capabilities by specifying this parameter\.The only valid values are `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_RESOURCE_POLICY`, and `CAPABILITY_AUTO_EXPAND`\.The following resources require you to specify `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`: [AWS::IAM::Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-group.html), [AWS::IAM::InstanceProfile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html), [AWS::IAM::Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), and [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html)\. If the application contains IAM resources, you can specify either `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`\. If the application contains IAM resources with custom names, you must specify `CAPABILITY_NAMED_IAM`\.The following resources require you to specify `CAPABILITY_RESOURCE_POLICY`: [AWS::Lambda::Permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-permission.html), [AWS::IAM:Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), [AWS::ApplicationAutoScaling::ScalingPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalingpolicy.html), [AWS::S3::BucketPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-policy.html), [AWS::SQS::QueuePolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sqs-policy.html), and [AWS::SNS::TopicPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sns-policy.html)\.Applications that contain one or more nested applications require you to specify `CAPABILITY_AUTO_EXPAND`\.If your application template contains any of the above resources, we recommend that you review all permissions associated with the application before deploying\. If you don't specify this parameter for an application that requires capabilities, the call will fail\. | 
| resourcesSupported | boolean | True | Whether all of the AWS resources contained in this application are supported in the region in which it is being retrieved\. | 

**See Also**
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/Version)
+ [AWS SDK for Go \- Pilot](/goto/SdkForGoPilot/serverlessrepo-2017-09-08/Version)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/Version)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/Version)
+ [AWS SDK for Ruby V2](/goto/SdkForRubyV2/serverlessrepo-2017-09-08/Version)