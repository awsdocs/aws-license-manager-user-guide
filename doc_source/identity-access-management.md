# Identity and access management for AWS License Manager<a name="identity-access-management"></a>

AWS Identity and Access Management \(IAM\) is an AWS service that helps an administrator securely control access to AWS resources\. IAM administrators control who can be authenticated \(signed in\) and authorized \(have permissions\) to use AWS resources\. With IAM you can create users and groups under your AWS account\. You control the permissions that users have to perform tasks using AWS resources\. You can use IAM for no additional charge\.

By default, IAM users don't have permissions for License Manager resources and operations\. To allow IAM users to manage License Manager resources, you must create an IAM policy that explicitly grants them permissions\. Then you attach the policy to the IAM users or groups that require those permissions\.

When you attach a policy to a user or group of users, it allows or denies the users permission to perform the specified tasks on the specified resources\. For more information, see [Policies and Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide* guide\.

## Policy structure<a name="iam-policy-structure"></a>

An IAM policy is a JSON document that consists of one or more statements\. Each statement is structured as follows\.

```
{
  "Statement":[{
    "Effect":"effect",
    "Action":"action",
    "Resource":"arn",
    "Condition":{
      "condition":{
        "key":"value"
        }
      }
    }
  ]
}
```

Various elements make up a statement:
+ **Effect:** The *effect* can be `Allow` or `Deny`\. By default, IAM users don't have permission to use resources and API operations, so all requests are denied\. An explicit *allow* overrides the default\. An explicit *deny* overrides any allows\.
+ **Action**: The *action* is the specific API operation for which you are granting or denying permission\.
+ **Resource**: The resource is affected by the action\. Some License Manager API operations allow you to include specific resources in your policy that can be created or modified by the operation\. To specify a resource in the statement, you need to use its Amazon Resource Name \(ARN\)\. For more information, see [Actions Defined by AWS License Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awslicensemanager.html#awslicensemanager-actions-as-permissions)\.
+ **Condition**: Conditions are optional\. They can be used to control when your policy is in effect\. For more information, see [Condition Keys for AWS License Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awslicensemanager.html#awslicensemanager-policy-keys)\.

## Policy for an ISV using License Manager<a name="vended-license-requirements"></a>

ISVs that distribute licenses through License Manager require the following permissions:

```
{ 
    "Version": "2012-10-17",     
    "Statement": [ 
        { 
        "Sid": "VisualEditor0", 
        "Effect": "Allow",
        "Action": [
            "license-manager:CreateLicense", 
            "license-manager:ListLicenses", 
            "license-manager:CreateLicenseVersion", 
            "license-manager:ListLicenseVersions", 
            "license-manager:GetLicense", 
            "license-manager:DeleteLicense", 
            "license-manager:CheckoutLicense", 
            "license-manager:CheckInLicense", 
            "kms:GetPublicKey"
        ], 
        "Resource": "*"
        } 
    ] 
}
```

## Example policies for License Manager<a name="iam-policy-examples"></a>

In an IAM policy statement, you can specify any API operation from any service that supports IAM\. For License Manager, use the following prefix with the name of the API operation: `license-manager:`\. For example:
+ `license-manager:CreateLicenseConfiguration`
+ `license-manager:ListLicenseConfigurations`

To specify multiple operations in a single statement, separate them with commas as follows:

```
"Action": ["license-manager:action1", "license-manager:action2"]
```

You can also specify multiple operations using wildcards\. For example, you can specify all License Manager API operations whose name begins with the word *List* as follows:

```
"Action": "license-manager:List*"
```

To specify all License Manager API operations, use the \* wildcard as follows:

```
"Action": "license-manager:*"
```