# Using Resource\-Based Policies for AWS Serverless Application Repository \(Application Policies\)<a name="access-control-resource-based"></a>

An AWS Serverless Application Repository application is the primary AWS resource in AWS Serverless Application Repository\. You can add permissions to the policy associated with an AWS Serverless Application Repository application\. Permissions policies attached to AWS Serverless Application Repository applications are referred to as *resource\-based policies* \(or *application policies*\)\. You can use AWS Serverless Application Repository application policies to manage application deployment permissions\.

**Important**  
Before you create resource\-based policies, we recommend that you first review the introductory topics that explain the basic concepts and options available for you to manage access to your AWS Serverless Application Repository resources\. For more information, see [Overview of Managing Access Permissions to Your AWS Serverless Application Repository Resources](access-control-overview.md)\.

AWS Serverless Application Repository application policies are primarily used by publishers to grant permission to consumers to deploy their applications\. Permissions can be granted using either the AWS CLI, the AWS SDKs, or the AWS Management Console\. The AWS CLI and the AWS SDKs allow publishers to set both course and fine\-grained permissions for their applications\. That is, publishers can set applications to be available for everyone, available to no one, and available only to a specific list of AWS accounts\. The AWS Management Console only allows publishers to set course permissions for their applications \(that is, available for everyone and available to no one\)\.

## Application Permissions<a name="application-permissions"></a>

This table contains the list of supported actions for setting permissions for AWS Serverless Application Repository applications when using the AWS CLI or the AWS SDKs\.


****  

| Action | Description | 
| --- | --- | 
| GetApplication |  Grants permission to view information about the application\.  | 
| CreateCloudFormationChangeSet |  Grants permission for the application to be deployed\. Note: This action does *not* grant any other permission other than to deploy\.  | 
| ListApplicationVersions | Grants permission to list the versions of the application\. | 
| SearchApplications | Grants permission for the application to be searched for\. | 
| Deploy |  This action enables all actions listed above, that is, it grants permission for the application to be viewed, deployed, versions to be listed, and to be searched for\.  | 

The examples below show how to grant permissions using the AWS CLI\. For information on how to grant permissions using the AWS Management Console see [Sharing an Application Through the Console](serverless-app-publishing-applications.md#share-application)\.

 AWS Serverless Application Repository provides the following AWS CLI commands to manage a permissions policy associated with an AWS Serverless Application Repository application:
+ [put\-application\-policy](http://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/put-application-policy.html)
+ [get\-application\-policy](http://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/get-application-policy.html)

## Example 1: Share an Application with Another Specific Account<a name="access-control-resource-based-example-share-with-specific-account"></a>

To share an application with another specific account, but keep it from being shared with others, you specify the AWS account ID you want to share with as the principal\. Following is the AWS CLI command to do this\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=account-id,Actions=Deploy
```

## Example 2: Share an Application Publicly<a name="access-control-resource-based-example-share-publicly"></a>

To make an application public, you share it with everyone by specifying "\*" as the principal, as in the following example\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=*,Actions=Deploy
```

## Example 3: Make an Application Private<a name="access-control-resource-based-example-make-private"></a>

You can make an application private, so it's not shared with anyone and can only be deployed by the AWS account that owns it\. To do so, you clear out the principals and actions from the policy, as follows\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements '[]'
```

## Example 4: Specifying Multiple Accounts and Permissions<a name="access-control-resource-based-example-multiple-permissions"></a>

Multiple permissions can be granted, and to more than one AWS account at a time\. This is done by specifying lists as the principal and actions, as in the following example\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=account-id-1,account-id-2,Actions=GetApplication,CreateCloudFormationChangeSet
```

## Example 5: Retrieve an Application Policy<a name="access-control-resource-based-example-retrieve-app-policy"></a>

To view an application's currently policy, for example to see whether it is currently being shared, you use the `get-application-policy` command, like in the following example\.

```
aws serverlessrepo get-application-policy \
--region region \
--application-id application-arn
```