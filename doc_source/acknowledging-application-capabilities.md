# Acknowledging IAM Roles, Resource Policies, and Nested Applications when Deploying Applications<a name="acknowledging-application-capabilities"></a>

Before you can deploy an application, the AWS Serverless Application Repository checks the application’s template for IAM roles, AWS resource policies, and nested applications that it might create\. IAM resources, such as an IAM role with full access, can modify any resource in your AWS account\. Therefore, we recommend that you review the permissions associated with the application before proceeding so that you don't unintentionally create resources with escalated permissions\. To ensure that you've done so, you must acknowledge that the application contains capabilities before the AWS Serverless Application Repository can deploy the application on your behalf\. 

Applications may contain any of the following four capabilities: `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_RESOURCE_POLICY`, and `CAPABILITY_AUTO_EXPAND`\.

The following resources require you to specify `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`: [AWS::IAM::Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-group.html), [AWS::IAM::InstanceProfile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html), [AWS::IAM::Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), and [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html)\. If the application contains IAM resources with custom names, you must specify `CAPABILITY_NAMED_IAM`\. See [Finding and Acknowledging Application Capabilities \(AWS CLI\)](#acknowledging-application-capabilities-api) for an example for how to specify capabilities\.

The following resources require you to specify `CAPABILITY_RESOURCE_POLICY`: [AWS::Lambda::Permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-permission.html), [AWS::IAM:Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), [AWS::ApplicationAutoScaling::ScalingPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalingpolicy.html), [AWS::S3::BucketPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-policy.html), [AWS::SQS::QueuePolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sqs-policy.html), and [AWS::SNS::TopicPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sns-policy.html)\.

Applications that contains one or more nested applications require you to specify `CAPABILITY_AUTO_EXPAND`\. For more information about nested applications see [Nested Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-nested-applications.html) in the *AWS Serverless Application Model Developer Guide*\.

## Finding and Acknowledging Application Capabilities \(Lambda console or AWS Website\)<a name="acknowledging-application-capabilities-console"></a>

You can find applications available in the AWS Serverless Application Repository on the [AWS Serverless Application Repository website](https://aws.amazon.com/serverless/serverlessrepo/) or through the [Lambda console in the **Create Function** page under the AWS Serverless Application Repository tab](https://console.aws.amazon.com/lambda/home?region=us-east-1#/create?tab=serverlessApps)\.

Applications that require acknowledgement of capabilities for creating custom IAM roles or resource policies are not shown in search results by default\. To search for applications that contain these capabilities, you must click the checkbox **Show apps that create custom IAM roles or resource policies**\.

You can review the capabilities of an application under the **Permissions** tab when you select the application\. To deploy the application, you need to click the checkbox: **I acknowledge this application creates custom IAM roles or resource policies**\. If you don’t acknowledge these capabilities, you will see the error message **Acknowledgement required\. To deploy, check the box in Configure application parameters section**\.

## Finding and Acknowledging Application Capabilities \(AWS CLI\)<a name="acknowledging-application-capabilities-api"></a>

To acknowledge an application's capabilities using the AWS CLI, follow these steps:

1. **Review the application's capabilities: **Use the following AWS CLI command to review an application's capabilities:

   ```
   aws serverlessrepo get-application \
   --application-id application-arn
   ```

   The [ requiredCapabilities response property](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid.html#applications-applicationid-prop-version-requiredcapabilities) will contain the list of application capabilities that you will need to acknowledge before you can deploy the application\. You can also use the [GetApplication API](https://docs.aws.amazon.com/goto/WebAPI/serverlessrepo-2017-09-08/GetApplication) in the AWS SDKs to get this data\.

1. **Deploy the application: **To deploy an application with capabilities, pass the list of its [capabilities](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid-changesets.html#applications-applicationid-changesets-createcloudformationchangesetinput-capabilities) when creating the AWS CloudFormation changeset\. For example, use the following AWS CLI command to deploy an application by acknowledging its capabilities:

   ```
   aws serverlessrepo create-cloud-formation-change-set \
   -–application-id application-arn \
   --stack-name unique-name-for-cloud-formation-stack \
   --capabilities list-of-capabilities
   ```

   You can also use the [CreateCloudFormationChangeSet API](https://docs.aws.amazon.com/goto/WebAPI/serverlessrepo-2017-09-08/CreateCloudFormationChangeSet) in the AWS SDKs to deploy the application\.

   **Example:**

   The following AWS CLI command acknowledges an application that contains an [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html) resource with a custom name and one or more nested applications:

   ```
   aws serverlessrepo create-cloud-formation-change-set \
   -–application-id application-arn \
   --stack-name unique-name-for-cloud-formation-stack \
   --capabilities CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND
   ```