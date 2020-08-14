# Applications applicationId<a name="applications-applicationid"></a>

## URI<a name="applications-applicationid-url"></a>

/applications/*applicationId*

## HTTP Methods<a name="applications-applicationid-http-methods"></a>

### GET<a name="applications-applicationidget"></a>

Operation ID: GetApplication

Gets the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Query Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
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

### DELETE<a name="applications-applicationiddelete"></a>

Operation ID: DeleteApplication

Deletes the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 204 | None | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 409 |  | The resource already exists\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

### PATCH<a name="applications-applicationidpatch"></a>

Operation ID: UpdateApplication

Updates the specified application\.


**Path Parameters**  

| Name | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | String | True | The Amazon Resource Name \(ARN\) of the application\. | 


**Responses**  

| Status Code | Response Model | Description | 
| --- |--- |--- |
| 200 |  | Success | 
| 400 |  | One of the parameters in the request is invalid\. | 
| 403 |  | The client is not authenticated\. | 
| 404 |  | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| 409 |  | The resource already exists\. | 
| 429 |  | The client is sending more than the allowed number of requests per unit of time\. | 
| 500 |  | The AWS Serverless Application Repository service encountered an internal error\. | 

## Schemas<a name="applications-applicationid-schemas"></a>

### Request Bodies<a name="applications-applicationid-request-examples"></a>

#### Example PATCH<a name="applications-applicationid-request-body-patch-example"></a>

```
{
  "description": "string",
  "author": "string",
  "readmeBody": "string",
  "readmeUrl": "string",
  "labels": [
    "string"
  ],
  "homePageUrl": "string"
}
```

### Response Bodies<a name="applications-applicationid-response-examples"></a>

#### Example Application<a name="applications-applicationid-response-body-application-example"></a>

```
{
  "applicationId": "string",
  "name": "string",
  "description": "string",
  "author": "string",
  "isVerifiedAuthor": boolean,
  "verifiedAuthorUrl": "string",
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
}
```

#### Example BadRequestException<a name="applications-applicationid-response-body-badrequestexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ForbiddenException<a name="applications-applicationid-response-body-forbiddenexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example NotFoundException<a name="applications-applicationid-response-body-notfoundexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example ConflictException<a name="applications-applicationid-response-body-conflictexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example TooManyRequestsException<a name="applications-applicationid-response-body-toomanyrequestsexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

#### Example InternalServerErrorException<a name="applications-applicationid-response-body-internalservererrorexception-example"></a>

```
{
  "message": "string",
  "errorCode": "string"
}
```

## Properties<a name="applications-applicationid-properties"></a>

### Application<a name="applications-applicationid-model-application"></a>

Details about the application\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | string | True | The application Amazon Resource Name \(ARN\)\. | 
| name | string | True | The name of the application\.Minimum length=1\. Maximum length=140Pattern: "\[a\-zA\-Z0\-9\\\\\-\]\+"; | 
| description | string | True | The description of the application\.Minimum length=1\. Maximum length=256 | 
| author | string | True | The name of the author publishing the app\.Minimum length=1\. Maximum length=127\.Pattern "^\[a\-z0\-9\]\(\(\[a\-z0\-9\]\|\-\(?\!\-\)\)\*\[a\-z0\-9\]\)?$"; | 
| isVerifiedAuthor | boolean | False | Specifies whether the author of this application has been verified\. This means that AWS has made a good faith review, as a reasonable and prudent service provider, of the information provided by the requester and has confirmed that the requester's identity is as claimed\. | 
| verifiedAuthorUrl | string | False | The URL to the public profile of a verified author\. This URL is submitted by the author\. | 
| spdxLicenseId | string | False | A valid identifier from https://spdx\.org/licenses/\. | 
| licenseUrl | string | False | A link to a license file of the app that matches the spdxLicenseID value of your application\.Maximum size 5 MB | 
| readmeUrl | string | False | A link to the readme file in Markdown language that contains a more detailed description of the application and how it works\.Maximum size 5 MB | 
| labels | Array of type string | False | Labels to improve discovery of apps in search results\.Minimum length=1\. Maximum length=127\. Maximum number of labels: 10Pattern: "^\[a\-zA\-Z0\-9\+\\\\\-\_:\\\\/@\]\+$"; | 
| creationTime | string | False | The date and time this resource was created\. | 
| homePageUrl | string | False | A URL with more information about the application, for example the location of your GitHub repository for the application\. | 
| version | [Version](#applications-applicationid-model-version) | False | Version information about the application\. | 

### BadRequestException<a name="applications-applicationid-model-badrequestexception"></a>

One of the parameters in the request is invalid\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | One of the parameters in the request is invalid\. | 
| errorCode | string | False | 400 | 

### Capability<a name="applications-applicationid-model-capability"></a>

Values that must be specified in order to deploy some applications\.
+ CAPABILITY\_IAM
+ CAPABILITY\_NAMED\_IAM
+ CAPABILITY\_AUTO\_EXPAND
+ CAPABILITY\_RESOURCE\_POLICY

### ConflictException<a name="applications-applicationid-model-conflictexception"></a>

The resource already exists\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource already exists\. | 
| errorCode | string | False | 409 | 

### ForbiddenException<a name="applications-applicationid-model-forbiddenexception"></a>

The client is not authenticated\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is not authenticated\. | 
| errorCode | string | False | 403 | 

### InternalServerErrorException<a name="applications-applicationid-model-internalservererrorexception"></a>

The AWS Serverless Application Repository service encountered an internal error\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The AWS Serverless Application Repository service encountered an internal error\. | 
| errorCode | string | False | 500 | 

### NotFoundException<a name="applications-applicationid-model-notfoundexception"></a>

The resource \(for example, an access policy statement\) specified in the request doesn't exist\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The resource \(for example, an access policy statement\) specified in the request doesn't exist\. | 
| errorCode | string | False | 404 | 

### ParameterDefinition<a name="applications-applicationid-model-parameterdefinition"></a>

Parameters supported by the application\.


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
| allowedValues | Array of type string | False | An array containing the list of values allowed for the parameter\. | 
| referencedByResources | Array of type string | True | A list of AWS SAM resources that use this parameter\. | 

### TooManyRequestsException<a name="applications-applicationid-model-toomanyrequestsexception"></a>

The client is sending more than the allowed number of requests per unit of time\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| message | string | False | The client is sending more than the allowed number of requests per unit of time\. | 
| errorCode | string | False | 429 | 

### UpdateApplicationInput<a name="applications-applicationid-model-updateapplicationinput"></a>

Update the application request\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| description | string | False | The description of the application\.Minimum length=1\. Maximum length=256 | 
| author | string | False | The name of the author publishing the app\.Minimum length=1\. Maximum length=127\.Pattern "^\[a\-z0\-9\]\(\(\[a\-z0\-9\]\|\-\(?\!\-\)\)\*\[a\-z0\-9\]\)?$"; | 
| readmeBody | string | False | A text readme file in Markdown language that contains a more detailed description of the application and how it works\.Maximum size 5 MB | 
| readmeUrl | string | False | A link to the readme file in Markdown language that contains a more detailed description of the application and how it works\.Maximum size 5 MB | 
| labels | Array of type string | False | Labels to improve discovery of apps in search results\.Minimum length=1\. Maximum length=127\. Maximum number of labels: 10Pattern: "^\[a\-zA\-Z0\-9\+\\\\\-\_:\\\\/@\]\+$"; | 
| homePageUrl | string | False | A URL with more information about the application, for example the location of your GitHub repository for the application\. | 

### Version<a name="applications-applicationid-model-version"></a>

Application version details\.


| Property | Type | Required | Description | 
| --- |--- |--- |--- |
| applicationId | string | True | The application Amazon Resource Name \(ARN\)\. | 
| semanticVersion | string | True | The semantic version of the application: [https://semver\.org/](https://semver.org/)  | 
| sourceCodeUrl | string | False | A link to a public repository for the source code of your application, for example the URL of a specific GitHub commit\. | 
| sourceCodeArchiveUrl | string | False | A link to the S3 object that contains the ZIP archive of the source code for this version of your application\.Maximum size 50 MB | 
| templateUrl | string | True | A link to the packaged AWS SAM template of your application\. | 
| creationTime | string | True | The date and time this resource was created\. | 
| parameterDefinitions | Array of type [ParameterDefinition](#applications-applicationid-model-parameterdefinition) | True | An array of parameter types supported by the application\. | 
| requiredCapabilities | Array of type [Capability](#applications-applicationid-model-capability) | True | A list of values that you must specify before you can deploy certain applications\. Some applications might include resources that can affect permissions in your AWS account, for example, by creating new AWS Identity and Access Management \(IAM\) users\. For those applications, you must explicitly acknowledge their capabilities by specifying this parameter\.The only valid values are `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_RESOURCE_POLICY`, and `CAPABILITY_AUTO_EXPAND`\.The following resources require you to specify `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`: [AWS::IAM::Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-group.html), [AWS::IAM::InstanceProfile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html), [AWS::IAM::Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), and [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html)\. If the application contains IAM resources, you can specify either `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`\. If the application contains IAM resources with custom names, you must specify `CAPABILITY_NAMED_IAM`\.The following resources require you to specify `CAPABILITY_RESOURCE_POLICY`: [AWS::Lambda::Permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-permission.html), [AWS::IAM:Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), [AWS::ApplicationAutoScaling::ScalingPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalingpolicy.html), [AWS::S3::BucketPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-policy.html), [AWS::SQS::QueuePolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sqs-policy.html), and [AWS::SNS::TopicPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sns-policy.html)\.Applications that contain one or more nested applications require you to specify `CAPABILITY_AUTO_EXPAND`\.If your application template contains any of the above resources, we recommend that you review all permissions associated with the application before deploying\. If you don't specify this parameter for an application that requires capabilities, the call will fail\. | 
| resourcesSupported | boolean | True | Whether all of the AWS resources contained in this application are supported in the region in which it is being retrieved\. | 

## See Also<a name="applications-applicationid-see-also"></a>

For more information about using this API in one of the language\-specific AWS SDKs and references, see the following:

### GetApplication<a name="GetApplication-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/GetApplication)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/GetApplication)

### DeleteApplication<a name="DeleteApplication-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/DeleteApplication)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/DeleteApplication)

### UpdateApplication<a name="UpdateApplication-see-also"></a>
+ [AWS Command Line Interface](/goto/aws-cli/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for \.NET](/goto/DotNetSDKV3/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for C\+\+](/goto/SdkForCpp/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for Go](/goto/SdkForGoV1/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for Java](/goto/SdkForJava/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for JavaScript](/goto/AWSJavaScriptSDK/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for PHP V3](/goto/SdkForPHPV3/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for Python](/goto/boto3/serverlessrepo-2017-09-08/UpdateApplication)
+ [AWS SDK for Ruby V3](/goto/SdkForRubyV3/serverlessrepo-2017-09-08/UpdateApplication)