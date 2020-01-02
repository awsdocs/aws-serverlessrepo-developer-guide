# AWS Serverless Application Repository Resource\-Based Policy Examples<a name="security_iam_resource-based-policy-examples"></a>

Permissions policies attached to AWS Serverless Application Repository applications are referred to as *resource\-based policies* \(or *application policies*\)\. Resource\-based policies determine the actions, and conditions required, that a specified principal can perform on an AWS Serverless Application Repository resource\.

An AWS Serverless Application Repository *application* is the primary AWS resource in the AWS Serverless Application Repository\. AWS Serverless Application Repository application policies are primarily used by publishers to grant permission to consumers to deploy their applications, and related operations such as to search for and view details of those applications\.

Publishers can set application permissions to the following three categories:
+ **Private** – Applications that were created with the same account, and haven't been shared with any other account\. Consumers have permission to deploy applications that were created using your AWS account\.
+ **Privately shared** – Applications that the publisher has explicitly shared with a specific set of AWS accounts\. Consumers have permission to deploy applications that have been shared with their AWS account\.
+ **Publicly shared** – Applications that the publisher has shared with everyone\. All consumers have permission to deploy any publicly shared application\.

**Note**  
For **privately shared applications**, the AWS Serverless Application Repository only supports *AWS accounts* as principals\. Publishers can grant or deny all users within an AWS account as a single group to an AWS Serverless Application Repository application\. Publishers cannot grant or deny individual users within an AWS account to an AWS Serverless Application Repository application\.

For instructions on setting application permissions using the AWS Management Console, see [Sharing an Application Through the Console](serverlessrepo-how-to-publish.md#share-application)\.

For instructions on setting application permissions using the AWS CLI and examples, see the following sections\.

## Application Permissions \(AWS CLI and AWS SDKs\)<a name="application-permissions"></a>

When you're using the AWS CLI or the AWS SDKs to set permissions for an AWS Serverless Application Repository application, you can specify the following actions:


****  

| Action | Description | 
| --- | --- | 
| GetApplication |  Grants permission to view information about the application\.  | 
| CreateCloudFormationChangeSet |  Grants permission for the application to be deployed\. Note: This action does *not* grant any other permission other than to deploy\.  | 
| CreateCloudFormationTemplate |  Grants permission to create an AWS CloudFormation template for the application\.  | 
| ListApplicationVersions | Grants permission to list the versions of the application\. | 
| ListApplicationDependencies | Grants permission to list the list applications that are nested in the containing application\. | 
| SearchApplications | Grants permission for the application to be searched for\. | 
| Deploy |  This action enables all the actions listed earlier in the table\. That is, it grants permission for the application to be viewed, for it to be deployed, for versions to be listed, and for it to be searched for\.  | 

## Resource\-Based Policy Examples<a name="access-control-resource-based-examples"></a>

The following examples show how to grant permissions by using the AWS CLI\. For information on how to grant permissions using the AWS Management Console, see [Sharing an Application Through the Console](serverlessrepo-how-to-publish.md#share-application)\.

All of the examples in this section use these AWS CLI commands to manage permissions policies associated with AWS Serverless Application Repository applications:
+ [put\-application\-policy](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/put-application-policy.html)
+ [get\-application\-policy](https://docs.aws.amazon.com/cli/latest/reference/serverlessrepo/get-application-policy.html)

**Topics**
+ [Example 1: Share an Application with Another Specific Account](#access-control-resource-based-example-share-with-specific-account)
+ [Example 2: Share an Application Publicly](#access-control-resource-based-example-share-publicly)
+ [Example 3: Make an Application Private](#access-control-resource-based-example-make-private)
+ [Example 4: Specifying Multiple Accounts and Permissions](#access-control-resource-based-example-multiple-permissions)
+ [Example 5: Retrieve an Application Policy](#access-control-resource-based-example-retrieve-app-policy)
+ [Example 6: Allow Application to Be Nested by Specific Accounts](#access-control-resource-based-example-nest-app-policy)

### Example 1: Share an Application with Another Specific Account<a name="access-control-resource-based-example-share-with-specific-account"></a>

To share an application with another specific account, but keep it from being shared with others, you specify the AWS account ID that you want to share with as the principal\. This is also known as setting the application to *privately shared*\. To do this, use the following AWS CLI command\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=account-id,Actions=Deploy
```

**Note**  
*Privately shared* applications can only be used in the same AWS Region where the application is created\.

### Example 2: Share an Application Publicly<a name="access-control-resource-based-example-share-publicly"></a>

To make an application public, you share it with everyone by specifying "\*" as the principal, as in the following example\. Applications that are shared publicly are available in all Regions\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=*,Actions=Deploy
```

**Note**  
In order to share an application publicly, it must meet the following requirements: 1\) It must be created in either us\-east\-1 or us\-east\-2, 2\) It must have the `SemanticVersion` property set, and 3\) It must have the `LicenseUrl` property set\.

### Example 3: Make an Application Private<a name="access-control-resource-based-example-make-private"></a>

You can make an application private, so it's not shared with anyone and can only be deployed by the AWS account that owns it\. To do so, you clear out the principals and actions from the policy, as follows\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements '[]'
```

**Note**  
*Private* applications can only be used in the same AWS Region where the application is created\.

### Example 4: Specifying Multiple Accounts and Permissions<a name="access-control-resource-based-example-multiple-permissions"></a>

You can grant multiple permissions, and you can grant them to more than one AWS account at a time\. To do this, you specify lists as the principal and actions, as shown in the following example\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=account-id-1,account-id-2,Actions=GetApplication,CreateCloudFormationChangeSet
```

### Example 5: Retrieve an Application Policy<a name="access-control-resource-based-example-retrieve-app-policy"></a>

To view an application's current policy \(for example, to see whether it's currently being shared\), use the `get-application-policy` command, as shown in the following example\.

```
aws serverlessrepo get-application-policy \
--region region \
--application-id application-arn
```

### Example 6: Allow Application to Be Nested by Specific Accounts<a name="access-control-resource-based-example-nest-app-policy"></a>

Public applications are allowed to be nested by anyone\. If you want to only allow your application to be nested by specific accounts, you must set the following minimal permissions, as shown in the following example\.

```
aws serverlessrepo put-application-policy \
--region region \
--application-id application-arn \
--statements Principals=account-id-1,account-id-2,Actions=GetApplication,CreateCloudFormationTemplate
```