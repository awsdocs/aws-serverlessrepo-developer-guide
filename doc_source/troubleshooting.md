# Troubleshooting the AWS Serverless Application Repository<a name="troubleshooting"></a>

When you use the AWS Serverless Application Repository, you might encounter issues when you create, update, or delete your applications\. Use this section to help troubleshoot common issues that you might encounter\. You can also search for answers and post questions in the [AWS Serverless Application Repository forums](https://forums.aws.amazon.com//forum.jspa?forumID=287)\.

**Note**  
Applications in the AWS Serverless Application Repository are deployed by using AWS CloudFormation\. For information on troubleshooting AWS CloudFormation issues, see the* [AWS CloudFormation Troubleshooting Guide](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html)\.*


+ [You Can't Make an Application Public](#issue-cant-make-app-public)
+ [A Limit Was Exceeded](#issue-limit-exceeded)
+ [Updating an Application's Readme File Doesn't Immediately Reflect on the Public Site](#issue-updating-readme-delay)
+ [You Can’t Deploy the Same Application Twice](#issue-cant-deploy-same-app-twice)
+ [Why Is My Application Not Publicly Available](#issue-why-not-publicly-available)
+ [Contacting Support](#issue-contacting-support)

## You Can't Make an Application Public<a name="issue-cant-make-app-public"></a>

If you can't make your application public, you might be missing a license file for your application that is approved by the Open Source Initiative \(OSI\)\.

To make your application public, you need an OSI\-approved license file, and also a successfully published version of the application with a source code URL for the version\. You can't update the license of an application after the application is created\. 

If you can't make your application public because you are missing a license file, delete the application and create a new one with the same name\. Make sure that you provide it with one or more open\-source licenses approved by the Open Source Initiative \(OSI\) organization\.

## A Limit Was Exceeded<a name="issue-limit-exceeded"></a>

If you receive an error message indicating that a limit was exceeded, check to see if you reached a resource limit\. For AWS Serverless Application Repository limits, see [AWS Serverless Application Repository Limits](limits.md)\.

## Updating an Application's Readme File Doesn't Immediately Reflect on the Public Site<a name="issue-updating-readme-delay"></a>

When you make your application public, the contents of your application can take up to 24 hours to update\. If you experience delays longer than 24 hours, try contacting AWS Support for help\. For details, see following\. 

## You Can’t Deploy the Same Application Twice<a name="issue-cant-deploy-same-app-twice"></a>

The application name that you provide is used as the name of the AWS CloudFormation stack\. If you have problems deploying an application, make sure that you don't have an existing AWS CloudFormation stack with the same name\. If you do, provide a different application name or delete the existing stack to deploy the application with the same name\.

## Why Is My Application Not Publicly Available<a name="issue-why-not-publicly-available"></a>

Applications are private by default\. In order to make your application public, follow the steps [here](http://docs.aws.amazon.com/serverlessrepo/latest/devguide/serverless-app-publishing-applications.html#share-application)\.

## Contacting Support<a name="issue-contacting-support"></a>

If you can't find troubleshooting solutions in this section or through the [AWS Serverless Application Repository forums](https://forums.aws.amazon.com//forum.jspa?forumID=287) and you have AWS Premium Support, you can create a technical support case at [AWS Support](https://console.aws.amazon.com/support/home#/)\. 

Before you contact AWS Support, make sure to get the Amazon Resource Name \(ARN\) for the application that you have questions about\. You can find the application ARN in the [AWS Serverless Application Repository Management Console](https://console.aws.amazon.com//serverlessrepo/)\.