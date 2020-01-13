# Updating Applications<a name="serverlessrepo-how-to-consume-new-version"></a>

After you've deployed an application from the AWS Serverless Application Repository, you might want to update it\. For example, you might want to change an application setting, or you might want to update the application to the latest version that was published\.

The following sections describe how to deploy a new version of an application by using either the AWS Management Console or the AWS CLI\.

## Updating Applications \(Console\)<a name="update-applications"></a>

To update an application that you previously deployed, use the same procedure as deploying a new application, and *provide the same application name that you originally deployed it with*\. In particular, the AWS Serverless Application Repository prepends `serverlessrepro-` to your application name\. However, to deploy a new version of your application, you provide the original application name without `serverlessrepo-` prepended\.

For example, if you deployed an application with the name `MyApplication`, the stack name would be `serverlessrepo-MyApplication`\. To update that application, you would provide the name `MyApplication` again—do *not* specify the full stack name of `serverlessrepo-MyApplication`\.

For all other application settings, you can either keep the values the same as the previous deployment, or provide new values\.

## Updating Applications \(AWS CLI\)<a name="update-applications-cli"></a>

To update an application that you previously deployed, use the same procedure as deploying a new application, and *provide the same `--stack-name` that you originally deployed it with*\. In particular, AWS Serverless Application Repository prepends `serverlessrepo-` to your stack name\. However, to deploy a new version of your application, you provide the original stack name without `serverlessrepo-` prepended\.

For example, if you deployed an application with the stack name `MyApplication`, the stack name that is created would be `serverlessrepo-MyApplication`\. To update that application, you would provide the name `MyApplication` again—do *not* specify the full stack name of `serverlessrepo-MyApplication`\.