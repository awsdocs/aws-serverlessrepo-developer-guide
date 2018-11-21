# Publishing Applications<a name="serverless-app-publishing-applications"></a>

Following, you can find how to make your serverless applications available for others to find and deploy\. You can publish serverless applications by using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or an AWS SDK\. 

To publish an application, you first upload the application code\. You also upload a simple manifest file, also known as an *AWS Serverless Application Model \(AWS SAM\) template\.* For more information about using AWS SAM, see [Using the AWS Serverless Application Model \(AWS SAM\)](using-aws-sam.md)\.

**Note**  
To make the serverless applications that you publish available to developers in other AWS Regions, publish your applications to either US East \(N\. Virginia\) \(us\-east\-1\) or US East \(Ohio\) \(us\-east\-2\)\. Publishing your application in any other AWS Region restricts its availability to that AWS Region\. For more information about AWS Serverless Application Repository regions and endpoints, see [Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#serverlessrepo_region) in the *AWS General Reference*\.

**Important**  
The information that you enter when publishing an application is not encrypted\. This information includes such data as the author name, location, and contact information\. If you have personally identifiable information that you don't want to be stored or made public, we recommend that you don't enter this information when publishing your application\.

## Prerequisites<a name="publishing-application-prerequisites"></a>

Before you publish an application to the AWS Serverless Application Repository, you need the following:
+ A valid AWS account\.
+ A valid AWS Serverless Application Model \(AWS SAM\) template that defines the AWS resources used\. For more information about AWS SAM templates, see the [AWS SAM Template Basics](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-basics.html)\. 
+ A package for your application that you created using the AWS CloudFormation `package` command for the AWS CLI\. This command packages the local artifacts \(local paths\) that your AWS SAM template references\. For more details, see [package](http://docs.aws.amazon.com/cli/latest/reference/cloudformation/package.html) in the AWS CloudFormation documentation\. 
+ A URL pointing to your application's source code, in case you want to publish your application publicly\.
+ A readme\.txt file\. This file should describe how customers can use your application, and how to configure it before deploying it in their own AWS accounts\. 
+ A license\.txt file\.
+ A valid Amazon S3 bucket policy that grants the service read permissions for artifacts uploaded to Amazon S3 when you packaged your application\. To do this, follow these steps:

  1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

  1. Choose the Amazon S3 bucket you used to package your application\.

  1. Choose the **Permissions** tab\.

  1. Choose the **Bucket Policy** button\.

  1. Paste the example policy statement below, making sure to substitute your bucket name in the Resource property value\.

  1. Choose the **Save** button\.

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

## Publishing an Application Through the AWS Management Console<a name="publishing-application-through-aws-console"></a>

You can create and publish an application through the AWS Management Console as described following\.

### Creating a New Application Through the Console<a name="create-new-application"></a>

Create a new application in the AWS Serverless Application Repository by using the following procedure\.

**To create a new application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home) and choose **Publish applications**\.

1. On the **Publish an application** page, type the indicated application information into the following boxes:
   + **Application Name**
   + **Author**
   + **Description**
   + **Search labels \(space delimited\)**
   + **SPDX license**
   + **Readme\.txt file**
   + **Semantic version**
   + **Source code URL** \(required only for publicly shared applications\)
   + **AWS SAM template file**

1. Choose **Publish application**\.

### Sharing an Application Through the Console<a name="share-application"></a>

Make your application publicly available using the following procedure\.

**To make your application publicly available**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you have created\.

1. Choose the application that you want to share\.

1. In the **Application Details** section, move the **Visibility** slider to **Application is public**\.

### Publishing a New Version of an Existing Application Through the Console<a name="publish-new-version-of-application"></a>

Publish a new version of an application that you already created using the following procedure\.

**To publish a new version of an application**

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you have created\.

1. Choose the application that you want to publish a new version for\.

1. Choose **Publish new version**\.

1. For **AWS SAM template file**, type the name of the new AWS SAM template file for this version\.

1. Choose **Publish**\.

## Publishing an Application Through the AWS CLI<a name="publishing-application-through-cli"></a>

You can create and publish an application through the AWS CLI as described following\.

### Creating a New Application Through the AWS CLI<a name="create-new-application-through-cli"></a>

To create a new application using the AWS CLI, first gather the same items required for publishing through the AWS Management Console, described preceding\. Then use the `aws serverlessrepo create-application` function, passing it each of these items as parameters\.

 For more information about the parameters to be passed to this function, type `aws serverlessrepo create-application help` at the AWS CLI\.

### Sharing an Application Through the AWS CLI<a name="share-application-through-cli"></a>

To make your application publicly available using the AWS CLI, you can use the `aws serverlessrepo put-application-policy` function, passing the application ID and policy statement as parameters\.

For more information about the parameters to be passed to this function, type `aws serverlessrepo put-application-policy help` at the AWS CLI\.

### Publishing a New Version of an Existing Application Through the AWS CLI<a name="publish-new-version-of-application-through-cli"></a>

To create a new version of an application using the AWS CLI, you can use the `aws serverlessrepo create-application-version` function\. You pass as parameters the application ID, semantic version, new SAM template, and source code URL\.

For more information about the parameters to be passed to this function, type `aws serverlessrepo create-application-version help` at the AWS CLI\.

## Deleting an Application Through the AWS Management Console<a name="deleting-application-through-aws-console"></a>

To delete a published application through the AWS Management Console, do the following\.

1. Open the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. For **My Applications**, choose the application that you want to delete\.

1. In the application's detail page, choose **Delete application**\. 

   A message appears\. 

1. Choose **Delete application** to complete the deletion\.

## Deleting an Application Through the AWS CLI<a name="deleting-application-through-cli"></a>

To delete a published application using the AWS CLI, you run the `[aws serverlessrepo delete\-application](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/delete-application.html)` command\. In the command, specify the application ID of the application that you want to delete\.

The following command deletes an application, where `<value>` is the application ID:

```
1. PROMPT> aws serverlessrepo delete-application --application-id <value>
```