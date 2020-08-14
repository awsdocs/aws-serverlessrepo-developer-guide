# Troubleshooting the AWS Serverless Application Repository<a name="troubleshooting"></a>

When you use the AWS Serverless Application Repository, you might encounter issues when you create, update, or delete your applications\. Use this section to help troubleshoot common issues that you might encounter\. You can also search for answers and post questions in the [AWS Serverless Application Repository forums](https://forums.aws.amazon.com/forum.jspa?forumID=287)\.

**Note**  
Applications in the AWS Serverless Application Repository are deployed by using AWS CloudFormation\. For information on troubleshooting AWS CloudFormation issues, see the* [AWS CloudFormation Troubleshooting Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html)\.*

**Topics**
+ [You Can't Make an Application Public](#issue-cant-make-app-public)
+ [A Quota Was Exceeded](#issue-limit-exceeded)
+ [An Updated Readme File Doesn't Appear Immediately](#issue-updating-readme-delay)
+ [You Can't Deploy an Application Due to Insufficient IAM Permissions](#issue-cant-deploy-app-due-to-insufficient-iam-permissions)
+ [You Can't Deploy the Same Application Twice](#issue-cant-deploy-same-app-twice)
+ [Why Is My Application Not Publicly Available](#issue-why-not-publicly-available)
+ [Contacting Support](#issue-contacting-support)

## You Can't Make an Application Public<a name="issue-cant-make-app-public"></a>

If you can't make your application public, you might be missing a license file for your application that is approved by the Open Source Initiative \(OSI\)\.

To make your application public, you need an OSI\-approved license file, and also a successfully published version of the application with a source code URL for the version\. You can't update the license of an application after the application is created\. 

If you can't make your application public because you are missing a license file, delete the application and create a new one with the same name\. Make sure that you provide it with one or more open\-source licenses approved by the Open Source Initiative \(OSI\) organization\.

## A Quota Was Exceeded<a name="issue-limit-exceeded"></a>

If you receive an error message that indicates that a quota was exceeded, check to see if you reached a resource quota\. For AWS Serverless Application Repository quotas, see [AWS Serverless Application Repository Quotas](quotas.md)\.

## An Updated Readme File Doesn't Appear Immediately<a name="issue-updating-readme-delay"></a>

When you make your application public, the contents of your application can take up to 24 hours to update\. If you experience delays longer than 24 hours, try contacting AWS Support for help\. For details, see following\. 

## You Can't Deploy an Application Due to Insufficient IAM Permissions<a name="issue-cant-deploy-app-due-to-insufficient-iam-permissions"></a>

To deploy an AWS Serverless Application Repository application, you need permissions to AWS Serverless Application Repository resources and AWS CloudFormation stacks\. You might also need permission to use the underlying services described in the application\. For example, if you're creating an Amazon S3 bucket or an Amazon DynamoDB table, you need permissions to Amazon S3 or DynamoDB\. 

If you run into this type of issue, review your AWS Identity and Access Management \(IAM\) policy and verify that you have the necessary permissions\. For more information, see [Controlling Access with AWS Identity and Access Management](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html)\. 

## You Can't Deploy the Same Application Twice<a name="issue-cant-deploy-same-app-twice"></a>

The application name that you provide is used as the name of the AWS CloudFormation stack\. If you have problems deploying an application, make sure that you don't have an existing AWS CloudFormation stack with the same name\. If you do, provide a different application name or delete the existing stack to deploy the application with the same name\.

## Why Is My Application Not Publicly Available<a name="issue-why-not-publicly-available"></a>

Applications are private by default\. In order to make your application public, follow the steps [here](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/serverless-app-publishing-applications.html#share-application)\.

## Contacting Support<a name="issue-contacting-support"></a>

In some cases, you might not be able to find troubleshooting solutions in this section or through the [AWS Serverless Application Repository forums](https://forums.aws.amazon.com/forum.jspa?forumID=287)\. If you have AWS Premium Support, you can create a technical support case at [AWS Support](https://console.aws.amazon.com/support/home#/)\. 

Before you contact AWS Support, make sure to get the Amazon Resource Name \(ARN\) for the application that you have questions about\. You can find the application ARN in the [AWS Serverless Application Repository console](https://console.aws.amazon.com/serverlessrepo/)\.