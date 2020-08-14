# Sharing Lambda Layers<a name="sharing-lambda-layers"></a>

If you've implemented functionality in a Lambda layer, you might want to share your layer without hosting a global instance of it\. Sharing layers in this manner enables others to deploy an instance of your layer to their own account\. This prevents client applications from depending on a global instance of your layer\. The AWS Serverless Application Repository enables you to share Lambda layers in this manner easily\.

For more information about Lambda layers, see [AWS Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html) in the *AWS Lambda Developer Guide*\.

## How It Works<a name="sharing-lambda-layers-how-it-works"></a>

The following are the steps for sharing your layer using the AWS Serverless Application Repository\. This allows a copy of your layer to be created in the user's AWS account\.

1. Define a serverless application with an AWS SAM template that includes your layer as a resource— that is, either an [https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-resource-layerversion.html](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-resource-layerversion.html) or an [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-layerversion.html](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-layerversion.html) resource\.

1. Publish your application to the AWS Serverless Application Repository, and share it \(either publicly or privately\)\.

1. A customer deploys your application, which creates a copy of your layer in their own AWS account\. The customer can now reference the Amazon Resource Name \(ARN\) of the layer in their AWS account in their client application\.

## Example<a name="sharing-layers-example"></a>

The following is an example AWS SAM template for an application that contains the Lambda layer that you want to share:

```
Resources:
  SharedLayer:
    Type: AWS::Serverless::LayerVersion
    Properties:
      LayerName: shared-layer
      ContentUri: source/layer-code/
      CompatibleRuntimes:
        - python3.7
Outputs:
  LayerArn:
    Value: !Ref SharedLayer
```

When a customer deploys your application from the AWS Serverless Application Repository, a layer is created in their AWS account\. The ARN of the layer looks something like the following:

`arn:aws:lambda:us-east-1:012345678901:layer:shared-layer:1`

The customer can now reference this ARN in their own client application, like in this example:

```
Resources:
  MyFunction:
    Type: AWS::Serverless::Function
    Properties:
      Handler: index.handler
      Runtime: python3.7
      CodeUrl: source/app-code/
      Layers:
        - arn:aws:lambda:us-east-1:012345678901:layer:shared-layer:1
```