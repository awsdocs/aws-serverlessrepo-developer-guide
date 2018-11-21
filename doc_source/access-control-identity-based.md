# Using Identity\-Based Policies \(IAM Policies\) for AWS Serverless Application Repository<a name="access-control-identity-based"></a>

You can use this topic to find examples of identity\-based policies in which an account administrator can attach permissions policies to IAM identities \(that is, users, groups, and roles\)\. 

**Important**  
We recommend that you first review the introductory topics that explain the basic concepts and options available for you to manage access to your AWS Serverless Application Repository resources\. For more information, see [Overview of Managing Access Permissions to Your AWS Serverless Application Repository Resources](access-control-overview.md)\.

You can find the following information in the sections in this topic:
+ [Permissions Required to Use the AWS Serverless Application Repository Console](#additional-console-required-permissions)
+ [Customer Managed Policy Examples](#access-policy-examples-customer-managed)

The following shows an example of a permissions policy\.

```
{

    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CreateApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:CreateApplication"
            ],
            "Resource": "*"
        },
        {
            "Sid": "CreateApplicationVersion",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:CreateApplicationVersion"
            ],
            "Resource": "arn:aws:serverlessrepo:region:account-id:applications/application-name"
        }
    ]
}
```

 The policy has two statements: 
+  The first statement grants permissions for the AWS Serverless Application Repository action `serverlessrepo:CreateApplication` on all AWS Serverless Application Repository resources, as specified by the wildcard character \(\*\) as the `Resource` value\. 
+ The second statement grants permission for the AWS Serverless Application Repository action `serverlessrepo:CreateApplicationVersion` on an AWS resource by using the Amazon Resource Name \(ARN\) for an AWS Serverless Application Repository application\. The application is specified by the `Resource` value\.

The policy doesn't specify the `Principal` element because in an identity\-based policy you don't specify the principal who gets the permission\. When you attach policy to a user, the user is the implicit principal\. When you attach a permission policy to an IAM role, the principal identified in the role's trust policy gets the permissions\.

 For a table showing all of the AWS Serverless Application Repository API operations and the AWS resources that they apply to, see [AWS Serverless Application Repository API Permissions: Actions and Resources Reference](serverlessrepo-api-permissions-ref.md)\. 

## Permissions Required to Use the AWS Serverless Application Repository Console<a name="additional-console-required-permissions"></a>

The AWS Serverless Application Repository console provides an integrated environment for you to discover and manage AWS Serverless Application Repository applications\. The console provides features and workflows that often require permissions to manage an AWS Serverless Application Repository application in addition to the API\-specific permissions documented in the [AWS Serverless Application Repository API Permissions: Actions and Resources Reference](serverlessrepo-api-permissions-ref.md)\.

For more information about these additional console permissions, see [Customer Managed Policy Examples](#access-policy-examples-customer-managed)\.

## Customer Managed Policy Examples<a name="access-policy-examples-customer-managed"></a>

The examples in this section provide a group of sample policies that you can attach to a user\. If you are new to creating policies, we recommend that you first create an IAM user in your account and attach the policies to the user in sequence\. This process is outlined in the steps in this section\.

You can use the console to verify the effects of each policy as you attach the policy to the user\. Initially, the user doesn't have permissions and can't do anything in the console\. As you attach policies to the user, you can verify that the user can perform various actions in the console\. 

We recommend that you use two browser windows: one to create the user and grant permissions, and the other to sign in to the AWS Management Console using the user's credentials and verify permissions as you grant them to the user\.

**Topics**
+ [Publisher Example 1: Allow a Publisher to List Applications](#access-control-identity-based-example-publisher-list-apps)
+ [Publisher Example 2: Allow a Publisher to View Details of an Application or Application Version](#access-control-identity-based-example-publisher-view-app-details)
+ [Publisher Example 3: Allow a Publisher to Create an Application or Application Version](#access-control-identity-based-example-publisher-create-apps)
+ [Publisher Example 4: Allow a Publisher to Create an Application Policy to Share Applications with Others](#access-control-identity-based-example-publisher-create-app-policies)
+ [Consumer Example 1: Allow a Consumer to Search for Applications](#access-control-identity-based-example-consumer-search-apps)
+ [Consumer Example 2: Allow a Consumer to View Details of an Application](#access-control-identity-based-example-consumer-view-app-details)
+ [Consumer Example 3: Allow a Consumer to Deploy an Application](#access-control-identity-based-example-consumer-deploy-apps)

### Publisher Example 1: Allow a Publisher to List Applications<a name="access-control-identity-based-example-publisher-list-apps"></a>

An IAM user in your account must have permissions for the serverlessrepo:ListApplications action before the user can see anything in the console\. When you grant these permissions, the console can show the list of AWS Serverless Application Repository applications in the AWS account created in the specific AWS Region the user belongs to\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListExistingApplications",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:ListApplications"
            ],
            "Resource": "*"
        }
    ]
}
```

### Publisher Example 2: Allow a Publisher to View Details of an Application or Application Version<a name="access-control-identity-based-example-publisher-view-app-details"></a>

A user can select an AWS Serverless Application Repository application and view details of the application\. Such details include author, description, versions, and other configuration information\. To do this, the user needs permissions for the `serverlessrepo:GetApplication` and `serverlessrepo:ListApplicationVersions` API operations for AWS Serverless Application Repository\. 

In the following example, these permissions are granted for the specific application whose Amazon Resource Name \(ARN\) is specified as the `Resource` value\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ViewApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:GetApplication",
                "serverlessrepo:ListApplicationVersions"
            ],
            "Resource": "arn:aws:serverlessrepo:region:account-id:applications/application-name"
        }
    ]
}
```

### Publisher Example 3: Allow a Publisher to Create an Application or Application Version<a name="access-control-identity-based-example-publisher-create-apps"></a>

If you want to allow a user permissions to create AWS Serverless Application Repository applications, you need to grant permissions to `serverlessrepo:CreateApplication` and `serverlessrepo:CreateApplicationVersions` operations, as shown in the following policy\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CreateApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:CreateApplication",
                "serverlessrepo:CreateApplicationVersion",
            ],
            "Resource": "*"
        }
    ]
}
```

### Publisher Example 4: Allow a Publisher to Create an Application Policy to Share Applications with Others<a name="access-control-identity-based-example-publisher-create-app-policies"></a>

In order for users to share applications with others, you must grant them permissions to create application policies, as with the following policy\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ShareApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:PutApplicationPolicy",
                "serverlessrepo:GetApplicationPolicy",
            ],
            "Resource": "*"
        }
    ]
}
```

### Consumer Example 1: Allow a Consumer to Search for Applications<a name="access-control-identity-based-example-consumer-search-apps"></a>

For consumers to search for applications, you must grant them the following permissions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "SearchApplications",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:SearchApplications"
            ],
            "Resource": "*"
        }
    ]
}
```

### Consumer Example 2: Allow a Consumer to View Details of an Application<a name="access-control-identity-based-example-consumer-view-app-details"></a>

A user can select an AWS Serverless Application Repository application and view details of the application, such as author, description, versions, and other configuration information\. To do so, the user must have permissions for the following AWS Serverless Application Repository operations\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ViewApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:GetApplication",
                "serverlessrepo:ListApplicationVersions"
            ],
            "Resource": "*"
        }
    ]
}
```

### Consumer Example 3: Allow a Consumer to Deploy an Application<a name="access-control-identity-based-example-consumer-deploy-apps"></a>

For customers to deploy applications, you must grant them permissions to perform a number of operations\. The following policy provides customers with the required permissions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DeployApplication",
            "Effect": "Allow",
            "Action": [
                "serverlessrepo:CreateCloudFormationChangeSet",
                "cloudformation:CreateChangeSet",
                "cloudformation:ExecuteChangeSet"
                "cloudformation:DescribeStacks"

            ],
            "Resource": "*"
        }
    ]
}
```

**Note**  
Deploying an application might require permissions to use additional AWS resources\. Because AWS Serverless Application Repository uses the same underlying deployment mechanism as AWS CloudFormation, you can see [Controlling Access with AWS Identity and Access Management](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html) for more information\. You can also see [ Troubleshooting: Insufficient IAM Permissions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/troubleshooting.html#troubleshooting-errors-insufficient-iam-permissions) for help with deployment issues related to permissions\.