# How to Publish Applications<a name="serverlessrepo-how-to-publish"></a>

This section provides you with procedures for publishing your serverless application to the AWS Serverless Application Repository using the AWS SAM CLI or the AWS Management Console\.

**Important**  
The information that you enter when you publish an application isn't encrypted\. This information includes such data as the author name\. If you have personally identifiable information that you don't want to be stored or made public, we recommend that you don't enter this information when publishing your application\.

## Publishing an Application Through the AWS SAM CLI<a name="publishing-application-through-cli"></a>

The easiest way to publish and share an application to the AWS Serverless Application Repository is to use a set of AWS SAM CLI commands\. For more information, see [Publishing an Application Using the AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-publishing-applications.html) in the *AWS Serverless Application Model \(AWS SAM\) Developer Guide*\.

## Publishing an Application Through the AWS Management Console<a name="publishing-application-through-aws-console"></a>

This section shows you how to use the AWS Management Console to publish an application to the AWS Serverless Application Repository\.

### Prerequisites<a name="publishing-application-prerequisites"></a>

Before you publish an application to the AWS Serverless Application Repository, you need the following:
+ A valid AWS account\.
+ A valid AWS Serverless Application Model \(AWS SAM\) template that defines the AWS resources used\. For more information about AWS SAM templates, see the [AWS SAM Template Basics](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-basics.html)\. 
+ A package for your application that you created using the AWS CloudFormation `package` command for the AWS CLI\. This command packages the local artifacts \(local paths\) that your AWS SAM template references\. For more details, see [package](http://docs.aws.amazon.com/cli/latest/reference/cloudformation/package.html) in the AWS CloudFormation documentation\. 
+ A URL pointing to your application's source code, in case you want to publish your application publicly\.
+ A readme\.txt file\. This file should describe how customers can use your application, and how to configure it before deploying it in their own AWS accounts\. 
+ A license\.txt file\.
+ A valid Amazon S3 bucket policy that grants the service read permissions for artifacts that were uploaded to Amazon S3 when you packaged your application\. To set this policy, follow these steps:

  1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

  1. Choose the Amazon S3 bucket you used to package your application\.

  1. Choose the **Permissions** tab\.

  1. Choose the **Bucket Policy** button\.

  1. Paste the following policy statement into the **Bucket policy editor**\. Make sure to substitute your bucket name in the Resource property value\.

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
     10.             "Resource": "arn:aws:s3:::<your-bucket-name>/*"
     11.         }
     12.     ]
     13. }
     ```

  1. Choose the **Save** button\.

### Creating a New Application Through the AWS Management Console<a name="create-new-application"></a>

Create a new application in the AWS Serverless Application Repository by using the following procedure\.

**To create a new application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home) and choose **Publish applications**\.

1. On the **Publish an application** page, enter the indicated application information in the following boxes:
   + **Application Name**
   + **Author**
   + **Description**
   + **Search labels \(space delimited\)**
   + **SPDX license**
   + **Readme\.txt file**
   + **Semantic version** \(required only for publicly shared applications\)
   + **Source code URL**
   + **AWS SAM template file**

1. Choose **Publish application**\.

### Sharing an Application Through the Console<a name="share-application"></a>

Make your application publicly available by using the following procedure\.

**To make your application publicly available**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you've created\.

1. Choose the application that you want to share\.

1. In the **Application Details** section, move the **Visibility** slider to **Application is public**\.

**Note**  
Using the console, you can only set applications to *private* or *publicly shared*\. If you want to set your application to *privately shared* so it's available only to a specific list of AWS accounts, see [Using Resource\-Based Policies for AWS Serverless Application Repository \(Application Policies\)](access-control-resource-based.md)\.

### Publishing a New Version of an Existing Application Through the Console<a name="publish-new-version-of-application"></a>

Publish a new version of an application that you already created by using the following procedure\.

**To publish a new version of an application**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you've created\.

1. Choose the application that you want to publish a new version for\.

1. Choose **Publish new version**\.

1. For **AWS SAM template file**, enter the name of the new AWS SAM template file for this version\.

1. Choose **Publish**\.

## Deleting an Application<a name="deleting-applications"></a>

You can delete applications from the AWS Serverless Application Repository by using either the AWS Management Console or the AWS SAM CLI\.

### Deleting an Application Through the AWS Management Console<a name="deleting-application-through-aws-console"></a>

To delete a published application through the AWS Management Console, do the following\.

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. For **My Applications**, choose the application that you want to delete\.

1. In the application's detail page, choose **Delete application**\. 

1. Choose **Delete application** to complete the deletion\.

### Deleting an Application Through the AWS CLI<a name="deleting-application-through-cli"></a>

To delete a published application using the AWS CLI, you run the `[aws serverlessrepo delete\-application](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/delete-application.html)` command\. In the command, specify the application ID of the application that you want to delete\.

The following command deletes an application, where `<value>` is the application ID:

```
1. PROMPT> aws serverlessrepo delete-application --application-id <value>
```