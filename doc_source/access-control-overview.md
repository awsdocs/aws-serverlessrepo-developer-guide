# Overview of Managing Access Permissions to Your AWS Serverless Application Repository Resources<a name="access-control-overview"></a>

Every AWS resource is owned by an AWS account, and permissions to create or access an AWS resource are governed by permissions policies\. An account administrator can attach permissions policies to IAM identities \(that is, users, groups, and roles\)\. Also, some services \(such as AWS Serverless Application Repository\) support attaching permissions policies to AWS resources\.

**Note**  
An *account administrator* \(or administrator user\) is a user with administrator privileges\. For more information, see [IAM Best Practices](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

When granting permissions, you decide who is getting the permissions, the AWS resources they get permissions for, and the specific actions that you want to allow on those AWS resources\.

**Topics**
+ [AWS Serverless Application Repository Resources and Operations](#access-control-resources)
+ [Understanding Resource Ownership](#access-control-resource-ownership)
+ [Managing Access to AWS Resources](#access-control-manage-access-intro)
+ [Specifying Policy Elements: Actions, Effects, AWS Resources, and Principals](#access-control-specify-lambda-actions)

## AWS Serverless Application Repository Resources and Operations<a name="access-control-resources"></a>

In AWS Serverless Application Repository, the primary AWS resource is an AWS Serverless Application Repository *application*\.

AWS Serverless Application Repository applications have unique Amazon Resource Names \(ARNs\) associated with them as shown in the following table\. 


****  

| AWS Resource Type | Amazon Resource Name \(ARN\) Format  | 
| --- | --- | 
| Application |  arn:aws:serverlessrepo:*region*:*account\-id*:applications/*application\-name*  | 

AWS Serverless Application Repository provides a set of operations to work with the AWS Serverless Application Repository resources\. For a list of available operations, see [Resources](resources.md)\.

## Understanding Resource Ownership<a name="access-control-resource-ownership"></a>

An *AWS resource owner* is the AWS account that created the AWS resource\. That is, the AWS resource owner is the AWS account of the *principal entity* \(the root account, an IAM user, or an IAM role\) that authenticates the request that creates the AWS resource\. The following examples illustrate how this works:
+ If you use the root account credentials of your AWS account to create an AWS Serverless Application Repository application, your AWS account is the owner of the AWS resource\. In AWS Serverless Application Repository, the AWS resource is the application\.
+ If you create an IAM user in your AWS account and grant permissions to create an AWS Serverless Application Repository application to that user, the user can create an application\. However, your AWS account, to which the user belongs, owns the AWS Serverless Application Repository application resource\.
+ If you create an IAM role in your AWS account with permissions to create an AWS Serverless Application Repository application, anyone who can assume the role can create an application\. Your AWS account, to which the role belongs, owns the AWS Serverless Application Repository application resource\. 

## Managing Access to AWS Resources<a name="access-control-manage-access-intro"></a>

A *permissions policy* describes who has access to what\. The following section explains the available options for creating permissions policies\.

**Note**  
This section discusses using IAM in the context of AWS Serverless Application Repository\. It doesn't provide detailed information about the IAM service\. For complete IAM documentation, see [What Is IAM?](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) in the *IAM User Guide*\. For information about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

Policies attached to an IAM identity are referred to as *identity\-based* policies \(IAM polices\) and policies attached to an AWS resource are referred to as *resource\-based* policies\. AWS Serverless Application Repository supports both identity\-based \(IAM policies\) and resource\-based policies\.

**Topics**
+ [Identity\-Based Policies \(IAM Policies\)](#access-control-manage-access-identity-based)
+ [Resource\-Based Policies \(AWS Serverless Application Repository Application Policies\)](#access-control-manage-access-resource-based)

### Identity\-Based Policies \(IAM Policies\)<a name="access-control-manage-access-identity-based"></a>

You can attach policies to IAM identities\. For example, you can do the following: 
+ **Attach a permissions policy to a user or a group in your account** – An account administrator can use a permissions policy that is associated with a particular user to grant permissions for that user to create an AWS Serverless Application Repository application\. 
+ **Attach a permissions policy to a role \(grant cross\-account permissions\)** – You can attach an identity\-based permissions policy to an IAM role to grant cross\-account permissions\. For example, the administrator in Account A can create a role to grant cross\-account permissions to another AWS account \(for example, Account B\) or an AWS service as follows:

  1. Account A administrator creates an IAM role and attaches a permissions policy to the role that grants permissions on AWS resources in Account A\.

  1. Account A administrator attaches a trust policy to the role identifying Account B as the principal who can assume the role\. 

  1. Account B administrator can then delegate permissions to assume the role to any users in Account B\. Doing this allows users in Account B to create or access AWS resources in Account A\. The principal in the trust policy can also be an AWS service principal if you want to grant an AWS service permissions to assume the role\.

   For more information about using IAM to delegate permissions, see [Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) in the *IAM User Guide*\.

The following is an example policy that grants permissions for the `serverlessrepo:ListApplications` action on all AWS resources\. In the current implementation, AWS Serverless Application Repository doesn't support identifying specific AWS resources using the AWS resource ARNs \(also referred to as resource\-level permissions\) for some of the API actions\. In these cases, you must specify a wildcard character \(\*\)\.

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

For more information about using identity\-based policies with AWS Serverless Application Repository, see [Using Identity\-Based Policies \(IAM Policies\) for AWS Serverless Application Repository](access-control-identity-based.md)\. For more information about users, groups, roles, and permissions, see [Identities \(Users, Groups, and Roles\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*\. 

### Resource\-Based Policies \(AWS Serverless Application Repository Application Policies\)<a name="access-control-manage-access-resource-based"></a>

Each AWS Serverless Application Repository application can have resource\-based permissions policies associated with it\. For AWS Serverless Application Repository, an application is the primary AWS resource and these policies are referred to as *AWS Serverless Application Repository application policies* or simply *application policies*\. For AWS Serverless Application Repository, you can use an application policy to allow another account to deploy applications you have published\. You can either allow deployments by a specific list of accounts \(private\), or you can allow deployments to all other accounts \(public\)\.

For more information about using resource\-based policies with AWS Serverless Application Repository, see [Using Resource\-Based Policies for AWS Serverless Application Repository \(Application Policies\)](access-control-resource-based.md)\. For additional information about using IAM roles \(identity\-based policies\) as opposed to resource\-based policies, see [How IAM Roles Differ from Resource\-based Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html) in the *IAM User Guide*\.

## Specifying Policy Elements: Actions, Effects, AWS Resources, and Principals<a name="access-control-specify-lambda-actions"></a>

For each AWS Serverless Application Repository resource \(see [AWS Serverless Application Repository Resources and Operations](#access-control-resources)\), the service defines a set of API operations \(see [Resources](resources.md)\)\. To grant permissions for these API operations, AWS Serverless Application Repository defines a set of actions that you can specify in a policy\. Performing an API operation can require permissions for more than one action\. When granting permissions for specific actions, you also identify the AWS resource on which the actions are allowed or denied\.

The following are the most basic policy elements\. In AWS Serverless Application Repository, we recommend defining policies using these elements only with identity\-based policies\.
+ **Resource** – In a policy, you use an Amazon Resource Name \(ARN\) to identify the AWS resource to which the policy applies\. For more information, see [AWS Serverless Application Repository Resources and Operations](#access-control-resources)\. 
+ **Action** – You use action keywords to identify AWS resource operations that you want to allow or deny\. For example, the `serverlessrepo:CreateApplication` permission allows the user permissions to perform the AWS Serverless Application Repository `CreateApplication` operation\. 
+ **Effect** – You specify the effect when the user requests the specific action—this can be either allow or deny\. If you don't explicitly grant access to \(allow\) an AWS resource, access is implicitly denied\. You can also explicitly deny access to an AWS resource, which you might do to make sure that a user cannot access it, even if a different policy grants access\.
+ **Principal** – In identity\-based policies \(IAM policies\), the user that the policy is attached to is the implicit principal\. For resource\-based policies, you specify the user, account, service, or other entity that you want to receive permissions \(applies to resource\-based policies only\)\. 

To learn more about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

For a table showing all of the AWS Serverless Application Repository API actions and the AWS resources that they apply to, see [AWS Serverless Application Repository API Permissions: Actions and Resources Reference](serverlessrepo-api-permissions-ref.md)\. 