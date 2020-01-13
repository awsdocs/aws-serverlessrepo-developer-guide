# Application Capabilities: IAM Roles, Resource Policies, and Nested Applications<a name="acknowledging-application-capabilities"></a>

Before you can deploy an application, the AWS Serverless Application Repository checks the application’s template for IAM roles, AWS resource policies, and nested applications that the template specifies that it should create\. IAM resources, such as an IAM role with full access, can modify any resource in your AWS account\. Therefore, we recommend that you review the permissions associated with the application before proceeding so that you don't unintentionally create resources with escalated permissions\. To ensure that you've done so, you must acknowledge that the application contains capabilities before the AWS Serverless Application Repository can deploy the application on your behalf\. 

Applications can contain any of the following four capabilities: `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_RESOURCE_POLICY`, and `CAPABILITY_AUTO_EXPAND`\.

The following resources require you to specify `CAPABILITY_IAM` or `CAPABILITY_NAMED_IAM`: [AWS::IAM::Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-group.html), [AWS::IAM::InstanceProfile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html), [AWS::IAM::Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), and [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html)\. If the application contains IAM resources with custom names, you must specify `CAPABILITY_NAMED_IAM`\. For an example of how to specify capabilities, see [Finding and Acknowledging Application Capabilities \(AWS CLI\)](serverlessrepo-how-to-consume.md#acknowledging-application-capabilities-api)\.

The following resources require you to specify `CAPABILITY_RESOURCE_POLICY`: [AWS::Lambda::LayerVersionPermission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-layerversionpermission.html), [AWS::Lambda::Permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-permission.html), [AWS::Events::EventBusPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-events-eventbuspolicy.html), [AWS::IAM:Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), [AWS::ApplicationAutoScaling::ScalingPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalingpolicy.html), [AWS::S3::BucketPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-policy.html), [AWS::SQS::QueuePolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sqs-policy.html), and [AWS::SNS::TopicPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sns-policy.html)\.

Applications that contain one or more nested applications require you to specify `CAPABILITY_AUTO_EXPAND`\. For more information about nested applications, see [Nested Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-nested-applications.html) in the *AWS Serverless Application Model Developer Guide*\.

## Finding and Acknowledging Application Capabilities \(Console\)<a name="acknowledging-application-capabilities-console"></a>

You can find applications available in the AWS Serverless Application Repository on the [AWS Serverless Application Repository website](https://aws.amazon.com/serverless/serverlessrepo/), or through the [Lambda console \(on the **Create Function** page under the AWS Serverless Application Repository tab\)](https://console.aws.amazon.com/lambda/home?region=us-east-1#/create?tab=serverlessApps)\.

Applications that require acknowledgment of capabilities for creating custom IAM roles or resource policies aren't shown in search results by default\. To search for applications that contain these capabilities, you must select the **Show apps that create custom IAM roles or resource policies** check box\.

You can review the capabilities of an application under the **Permissions** tab when you select the application\. To deploy the application, you need to select the **I acknowledge this application creates custom IAM roles or resource policies** check box\. If you don’t acknowledge these capabilities, you see this error message: **Acknowledgement required\. To deploy, check the box in Configure application parameters section**\.

## Viewing Application Capabilities \(AWS CLI\)<a name="acknowledging-application-capabilities-cli"></a>

To view an application's capabilities using the AWS CLI, you first need the application's Amazon Resource Name \(ARN\)\. You can then execute the following command:

```
aws serverlessrepo get-application \
--application-id application-arn
```

The [ requiredCapabilities](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid.html#applications-applicationid-prop-version-requiredcapabilities) response property contains the list of application capabilities that you need to acknowledge before you can deploy the application\. Note that if the [requiredCapabilities](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid.html#applications-applicationid-prop-version-requiredcapabilities) property is empty, the application has no required capabilities\.