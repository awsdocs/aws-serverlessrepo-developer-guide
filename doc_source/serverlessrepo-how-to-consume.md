# How to Deploy Applications<a name="serverlessrepo-how-to-consume"></a>

This section provides you with procedures for deploying serverless applications from the AWS Serverless Application Repository by using the AWS Management Console or the AWS CLI\.

## Deploying a New Application \(Console\)<a name="consuming-applications-console"></a>

This section shows you how to deploy a new application from the AWS Serverless Application Repository using the AWS Management Console\. For instructions on deploying a new version of an existing application, see [Updating Applications](serverlessrepo-how-to-consume-new-version.md)\.

### Browsing, Searching, and Deploying Applications<a name="browse-and-search-applications"></a>

Find, configure, and deploy an application in the AWS Serverless Application Repository by using the following procedure\.

**To find and configure an application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository public home page](https://aws.amazon.com/serverless/serverlessrepo), or open the [AWS Lambda console](https://console.aws.amazon.com/lambda/)\. Choose **Create function**, and then choose **Browse serverless app repository**\.

1. Browse or search for an application\.
**Note**  
To show applications that contain custom IAM roles or resource policies, select the **Show apps that create custom IAM roles or resource policies** check box\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. Choose an application to view details such as its permissions, capabilities, and the number of times it has been deployed by AWS customers\. 

   The deployment counts are shown for the AWS Region that you're trying to deploy the application in\.

1. On the application detail page, view the application's permissions and application resources by viewing the AWS SAM template, license, and readme file\. On this page, you can also find the **Source code URL** link for applications that are publicly shared\. If the application includes any nested applications, you can also view details of the nested applications on this page\.

1. Configure the application in the **Application settings** section\. For guidance on configuring a particular application, see that application’s readme file\. 

   For example, configuration requirements might include specifying the name of a resource that you want the application to have access to\. Such a resource might be an Amazon DynamoDB table, an Amazon S3 bucket, or an Amazon API Gateway API\.

1. Choose **Deploy**\. Doing this takes you to the **Deployment status** page\.
**Note**  
If the application has capabilities that require acknowledgement, you must select the **I acknowledge this application creates custom IAM roles or resource polices** check box before deploying the application\. Otherwise, an error will result\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. On the **Deployment status** page, you can view the progress of your deployment\. While waiting for your deployment to complete, you can search and browse for other applications, and return to this page through the Lambda console\.

After your application has been successfully deployed, you can review and manage the resources that have been created by using existing AWS tools\. 

## Deploying a New Application \(AWS CLI\)<a name="consuming-applications-cli"></a>

This section shows you how to deploy a new application from the AWS Serverless Application Repository by using the AWS CLI\. For instructions on deploying a new version of an existing application, see [Updating Applications](serverlessrepo-how-to-consume-new-version.md)\.

### Finding and Acknowledging Application Capabilities \(AWS CLI\)<a name="acknowledging-application-capabilities-api"></a>

To acknowledge an application's capabilities using the AWS CLI, follow these steps:

1. **Review the application's capabilities\. **Use the following AWS CLI command to review an application's capabilities:

   ```
   aws serverlessrepo get-application \
   --application-id application-arn
   ```

   The [requiredCapabilities](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid.html#applications-applicationid-prop-version-requiredcapabilities) response property contains the list of application capabilities that you need to acknowledge before you can deploy the application\. You can also use the [GetApplication API](https://docs.aws.amazon.com/goto/WebAPI/serverlessrepo-2017-09-08/GetApplication) in the AWS SDKs to get this data\.

1. **Create the changeset\. **You must provide the set of required [capabilities](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid-changesets.html#applications-applicationid-changesets-createcloudformationchangesetinput-capabilities) when you create the AWS CloudFormation changeset\. For example, use the following AWS CLI command to deploy an application by acknowledging its capabilities:

   ```
   aws serverlessrepo create-cloud-formation-change-set \
   -–application-id application-arn \
   --stack-name unique-name-for-cloud-formation-stack \
   --capabilities list-of-capabilities
   ```

   The changeset ID is returned when this command is successfully executed\. You need the changeset ID for the next step\. You can also use the [CreateCloudFormationChangeSet API](https://docs.aws.amazon.com/goto/WebAPI/serverlessrepo-2010-05-15/CreateCloudFormationChangeSet) in the AWS SDKs to create the changeset\.

   For example, the following AWS CLI command acknowledges an application that contains an [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html) resource with a custom name and one or more nested applications:

   ```
   aws serverlessrepo create-cloud-formation-change-set \
   -–application-id application-arn \
   --stack-name unique-name-for-cloud-formation-stack \
   --capabilities CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND
   ```

1. **Execute the changeset\. **Executing the changeset actually performs the deployment\. Provide the changeset ID that was returned when you created the changeset in the previous step\.

   The following example AWS CLI command executes the application changeset to deploy the application:

   ```
   aws cloudformation execute-change-set \
   -–change-set-name changeset-id-arn
   ```

   You can also use the [ExecuteChangeSet API](https://docs.aws.amazon.com/goto/WebAPI/cloudformation-2010-05-15/CreateChangeSet) in the AWS SDKs to execute the changeset\.

## Deleting Application Stacks<a name="delete-application-stack"></a>

To delete an application that you previously deployed using the AWS Serverless Application Repository, follow the same procedure as for deleting an AWS CloudFormation stack:
+ **AWS Management Console**: To delete an application using the AWS Management Console, see [Deleting a Stack on the AWS CloudFormation Console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-delete-stack.html) in the *AWS CloudFormation User Guide\.*
+ **AWS CLI**: To delete an application using the AWS CLI, see [Deleting a Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-cli-deleting-stack.html) in the *AWS CloudFormation User Guide\.*