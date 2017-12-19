# Publishing Applications \(Preview\)<a name="serverless-app-publishing-applications"></a>


|  | 
| --- |
|  To request access to the AWS Serverless ApplicationRepository, [sign up for the Preview](https://pages.awscloud.com/serverlessrepo-preview.html)\.   | 

Following, you can find out how to make your serverless applications available for others to find and deploy\. You can publish serverless applications by using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or an AWS SDK\. 

To publish an application, you upload the application code\. With the code, you upload a simple manifest file, also known as an *AWS Serverless Application Model \(AWS SAM\) template\.* For more information about using AWS SAM, see [Using the AWS Serverless Application Model \(AWS SAM\)](using-aws-sam.md)\.

**Note**  
To make the serverless applications that you publish available to developers in other AWS Regions, publish your applications to either US East \(N\. Virginia\) \(us\-east\-1\) or US East \(Ohio\) \(us\-east\-2\)\. Publishing your application in any other AWS Region restricts its availability to that AWS Region\.

Before you publish an application to the AWS Serverless ApplicationRepository, you need the following:

+ A valid AWS account\.

+ A valid AWS Serverless Application Model \(AWS SAM\) template that defines the AWS resources used\. For more information about SAM, see [AWS Serverless Application Model \(AWS SAM\)](https://github.com/awslabs/serverless-application-model)\.

+ A package for your application that you created using the AWS CloudFormation `package` AWS CLI command\. This command packages the local artifacts \(local paths\) that your AWS SAM template references\. For more details, see [package](http://docs.aws.amazon.com/cli/latest/reference/cloudformation/package.html) in the AWS CloudFormation documentation\. 

+ A URL pointing to your application's source code, should you want to publish your application publicly\.

+ A readme\.txt file\. This file should describe how customers can use your application, and how to configure it before deploying it in their own AWS accounts\. 

+ A license\.txt file\.

## Publishing an Application Through the AWS Management Console<a name="publishing-application-through-aws-console"></a>

### Creating a New Application Through the Console<a name="create-new-application"></a>

Create a new application in the AWS Serverless ApplicationRepository by using the following console procedure\.

**To create a new application in the AWS Serverless ApplicationRepository**

1. Because this feature is in Preview, first make sure that you are [signed up for the Preview](https://pages.awscloud.com/serverlessrepo-preview.html)\.

1. After you are approved for the Preview, sign in to the AWS Serverless ApplicationRepository console using the link provided in your acceptance email\.

1. On the **Create Application** page, type the indicated application information into the following boxes:

   + **Publisher Name**

   + **Application Name**

   + **Description**

   + **Source code URL** \(required only for publicly shared applications\)

   + **License\.txt file**

   + **Readme\.txt file**

   + **AWS SAM template file**

   + **Search labels \(space delimited\)**

1. Choose **Create Application**\.

### Sharing an Application Through the Console<a name="share-application"></a>

Make your application publicly available using the following procedure\.

**To make your application publicly available**

1. Open the [AWS Serverless ApplicationRepository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you have created\.

1. Choose the application that you want to share\.

1. In the **Application Details** section, move the **Visibility** slider to **Application is public**\.

### Publishing a New Version of an Existing Application Through the Console<a name="publish-new-version-of-application"></a>

Publish a new version of an application that you already created using the following procedure\.

**To publish a new version of an application**

1. Open the [AWS Serverless ApplicationRepository console](https://console.aws.amazon.com/serverlessrepo/home)\.

1. On the navigation pane, choose **My Applications** to bring up the list of applications that you have created\.

1. Choose the application that you want to publish a new version for\.

1. Choose **Publish new version**\.

1. For **AWS SAM template file**, type the name of the new AWS SAM template file for this version\.

1. Choose **Publish**\.