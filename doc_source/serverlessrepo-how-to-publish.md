# How to Publish Applications<a name="serverlessrepo-how-to-publish"></a>

This section provides you with procedures for publishing your serverless application to the AWS Serverless Application Repository by using the AWS SAM CLI or the AWS Management Console\. It also shows you how to share your application to allow others to deploy it, and deleting your application from the AWS Serverless Application Repository\.

**Important**  
The information that you enter when you publish an application isn't encrypted\. This information includes data such as the author name\. If you have personally identifiable information that you don't want to be stored or made public, we recommend that you don't enter this information when publishing your application\.

## Publishing an Application \(AWS CLI\)<a name="publishing-application-through-cli"></a>

The easiest way to publish an application to the AWS Serverless Application Repository is to use a set of AWS SAM CLI commands\. For more information, see [Publishing an Application Using the AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-publishing-applications.html) in the *AWS Serverless Application Model \(AWS SAM\) Developer Guide*\.

## Publishing a New Application \(Console\)<a name="publishing-application-through-aws-console"></a>

This section shows you how to use the AWS Management Console to publish a new application to the AWS Serverless Application Repository\. For instructions on publishing a new version of an existing application, see [Publishing a New Version of an Existing Application](serverlessrepo-how-to-publish-new-version.md)\.

### Prerequisites<a name="publishing-application-prerequisites"></a>

Before you publish an application to the AWS Serverless Application Repository, you need the following:
+ A valid AWS account\.
+ A valid AWS Serverless Application Model \(AWS SAM\) template that defines the AWS resources that are used\. For more information about AWS SAM templates, see [AWS SAM Template Basics](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-basics.html)\. 
+ A package for your application that you created by using the AWS CloudFormation `package` command for the AWS CLI\. This command packages the local artifacts \(local paths\) that your AWS SAM template references\. For more details, see [package](http://docs.aws.amazon.com/cli/latest/reference/cloudformation/package.html) in the AWS CloudFormation documentation\. 
+ A URL that points to your application's source code, in case you want to publish your application publicly\.
+ A readme\.txt file\. This file should describe how customers can use your application, and how to configure it before deploying it in their own AWS accounts\. 
+ A license\.txt file or a valid license identifier from the [SPDX website](https://spdx.org/licenses/)\. Note that a license is only required if you want to share your application publicly\. If you're going to keep your application private or only share it privately, you don't need to specify a license\.
+ A valid Amazon S3 bucket policy that grants the service read permissions for artifacts that were uploaded to Amazon S3 when you packaged your application\. To set this policy, follow these steps:

  1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

  1. Choose the Amazon S3 bucket that you used to package your application\.

  1. Choose the **Permissions** tab\.

  1. Choose the **Bucket Policy** button\.

  1. Paste the following policy statement into the **Bucket policy editor**\. Make sure to substitute your bucket name in the `Resource` property value\.

     ```
      1. {
      2.     "Version": "2012-10-17",
      3.     "Statement": [
      4.         {
      5.             "Effect": "Allow",
      6.             "Principal": {
      7.                 "Service":  "serverlessrepo.amazonaws.com"
      8.             },
      9.             "Action": "s3:GetObject",
     10.             "Resource": "arn:aws:s3:::bucketname/*"
     11.         }
     12.     ]
     13. }
     ```

  1. Choose the **Save** button\.

### Procedure<a name="create-new-application"></a>

Create a new application in the AWS Serverless Application Repository by using the following procedure\.

**To create a new application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home) and choose **Publish applications**\.

1. On the **Publish an application** page, enter the following application information, and then choose **Publish application**:    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/serverlessrepo/latest/devguide/serverlessrepo-how-to-publish.html)

## Sharing an Application<a name="share-application"></a>

Published applications can have permissions set in one of the three following categories:
+ **Private \(default\)** – Applications that were created with the same account, and haven't been shared with any other AWS account\. Only consumers that share your AWS account have permission to deploy private applications\.
+ **Privately shared** – Applications that the publisher has explicitly shared with a specific set of AWS accounts, or with AWS accounts in an AWS Organization\. Consumers have permission to deploy applications that have been shared with their AWS account or AWS Organization\. For more information about AWS Organizations, see the *[AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/)*\.
+ **Publicly shared** – Applications that the publisher has shared with everyone\. All consumers have permission to deploy any publicly shared application\.

After you have published an application to the AWS Serverless Application Repository, by default it is set to **private**\. This section shows you how to share an application privately with specific AWS accounts or an AWS Organization, or share it publicly with everyone\.

### Sharing an Application Through the Console<a name="share-application-console"></a>

You have two options for sharing your application with others: 1\) Share it with specific AWS accounts or the AWS accounts within your AWS organization, or 2\) Share it publicly with everyone\. For more information about AWS Organizations, see the *[AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/)*\.

**Option 1: To share your application with specific AWS account\(s\) or accounts within your AWS organization**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **Published Applications** to bring up the list of applications that you've created\.

1. Choose the application that you want to share\.

1. Choose the **Sharing** tab\.

1. In the **Application policy statements** section, choose the **Create Statement** button\.

1. In the **Statement Configuration** window fill out the fields based on how you want to share your application\.
**Note**  
If you are sharing with an organization, you can only specify the organization that your AWS account is a member of\. If you try to specify an AWS Organization that you are not a member of, an error will result\.  
To share your application with your AWS Organization, you must acknowledge that the `UnshareApplication` action will be added to your policy statement, in case the sharing needs to be revoked in the future\.

1. Choose the **Save** button\.

**Option 2: To share your application publicly with everyone**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **Published Applications** to bring up the list of applications that you've created\.

1. Choose the application that you want to share\.

1. Choose the **Sharing** tab\.

1. In the **Public Sharing** section, choose the **Edit** button\.

1. Under **Public sharing** choose the **Enabled** radio button\.

1. In the text box type the name of your application, then choose the **Save** button\.

**Note**  
In order to share an application publicly, it must have both the `SemanticVersion` and `LicenseUrl` properties set\.

### Sharing an Application Through the AWS CLI<a name="share-application-cli"></a>

To share an application using the AWS CLI you grant permissions using the `[put\-application\-policy](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/put-application-policy.html)` command to specify the AWS account\(s\) you want to share with as principals\.

For more information about sharing your application by using the AWS CLI, see [AWS Serverless Application Repository Resource\-Based Policy Examples](security_iam_resource-based-policy-examples.md)\.

## Unsharing an Application<a name="unshare-applications"></a>

There are two options for unsharing an application from an AWS Organization:

1. The publisher of the application can remove permissions using the `[put\-application\-policy](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/put-application-policy.html)` command\.

1. A user from the *master account* of an AWS Organization can perform an [unshare application](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/applications-applicationid-unshare.html) operation on any application shared with the organization, even if the application was published by a user from a different account\.
**Note**  
When an application is unshared from an AWS Organization with the "unshare application" operation, it cannot be shared with AWS Organization again\.

   For more information about AWS Organizations, see the *[AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/)*\.

### Publisher Removing Permissions<a name="unshare-applications-publisher"></a>

#### Publisher Removing Permissions Through the Console<a name="unshare-application-publisher-console"></a>

To unshare an application through the AWS Management Console, you remove the policy statement that shares it with other AWS accounts\. To do this, follow these steps:

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. Choose **Available Applications** in the left navigation pane\.

1. Choose the application that you want to unshare\.

1. Choose the **Sharing** tab\.

1. In the **Application policy statements** section, select the policy statement that is sharing the application with the accounts that you want to unshare from\.

1. Choose **Delete**\.

1. A confirmation message will appear\. Choose **Delete** again\.

#### Publisher Removing Permissions Through the AWS CLI<a name="unshare-application-publisher-cli"></a>

To unshare an application through the AWS CLI, the publisher can remove or otherwise change permissions using the `[put\-application\-policy](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/put-application-policy.html)` command to make the application private, or share with a different set of AWS accounts\.

For more information about changing permissions using the AWS CLI, see [AWS Serverless Application Repository Resource\-Based Policy Examples](security_iam_resource-based-policy-examples.md)\.

### Master Account Unsharing an Application<a name="unshare-applications-master"></a>

#### Master Account Unsharing an Application from an AWS Organization Through the Console<a name="unshare-application-master-console"></a>

To unshare an application from an AWS Organization through the AWS Management Console, a user from the *master account* can do the following:

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. Choose **Available Applications** in the left navigation pane\.

1. In the application's tile, choose **Unshare**\.

1. In the unshare message box, confirm you want to unshare the application by entering the Organization ID and application name, then choosing **Save**\.

#### Master Account Unsharing an Application from an AWS Organization Through the AWS CLI<a name="unshare-application-master-cli"></a>

To unshare an application from an AWS Organization, a user from the *master account* can run the `aws serverlessrepo unshare-application` command\.

The following command unshares an application from an AWS Organization, where *application\-id* is the Amazon Resource Name \(ARN\) of the application, and *organization\-id* is the AWS Organization ID:

```
1. aws serverlessrepo unshare-application --application-id application-id --organization-id organization-id
```

## Deleting an Application<a name="deleting-applications"></a>

You can delete applications from the AWS Serverless Application Repository by using either the AWS Management Console or the AWS SAM CLI\.

### Deleting an Application \(Console\)<a name="deleting-application-through-aws-console"></a>

To delete a published application through the AWS Management Console, do the following\.

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. For **My Applications**, choose the application that you want to delete\.

1. In the application's detail page, choose **Delete application**\. 

1. Choose **Delete application** to complete the deletion\.

### Deleting an Application \(AWS CLI\)<a name="deleting-application-through-cli"></a>

To delete a published application using the AWS CLI, run the `[aws serverlessrepo delete\-application](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/delete-application.html)` command\.

The following command deletes an application, where `application-id` is the Amazon Resource Name \(ARN\) of the application:

```
1. aws serverlessrepo delete-application --application-id application-id
```