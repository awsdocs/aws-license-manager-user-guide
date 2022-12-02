# AWS managed policies for AWS License Manager<a name="security-iam-awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ReadOnlyAccess** AWS managed policy provides read\-only access to all AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

## AWS managed policy: AWSLicenseManagerServiceRolePolicy<a name="security-iam-AWSLicenseManagerServiceRolePolicy"></a>

This policy is attached to the service\-linked role named **AWSServiceRoleForAWSLicenseManagerRole** to allow License Manager to call API actions to manage licenses on your behalf\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.

To view the permissions for this policy, see in the [AWSLicenseManagerServiceRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSLicenseManagerServiceRolePolicy)\.

## AWS managed policy: AWSLicenseManagerMasterAccountRolePolicy<a name="security-iam-AWSLicenseManagerMasterAccountRolePolicy"></a>

This policy is attached to the service\-linked role named **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** to allow License Manager to call API actions to manage license management for a central management account on your behalf\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.

To view the permissions for this policy, see in the [AWSLicenseManagerMasterAccountRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSLicenseManagerMasterAccountRolePolicy)\.

## AWS managed policy: AWSLicenseManagerMemberAccountRolePolicy<a name="security-iam-AWSLicenseManagerMemberAccountRolePolicy"></a>

This policy is attached to the service\-linked role named **AWSServiceRoleForAWSLicenseManagerMemberAccountRole** to allow License Manager to call API actions for license management from a configured management account on your behalf\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.

To view the permissions for this policy, see in the [AWSLicenseManagerMemberAccountRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSLicenseManagerMemberAccountRolePolicy)\.

## AWS managed policy: AWSLicenseManagerConsumptionPolicy<a name="security-iam-AWSLicenseManagerConsumptionPolicy"></a>

You can attach the `AWSLicenseManagerConsumptionPolicy` policy to your IAM identities\. This policy grants permissions that allow access to the License Manager API actions required to consume licenses\. For more information, see [License usage](seller-issued-licenses.md#license-usage)\.

To view the permissions for this policy, see [AWSLicenseManagerConsumptionPolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSLicenseManagerConsumptionPolicy) in the AWS Management Console\.

## AWS managed policy: AWSLicenseManagerUserSubscriptionsServiceRolePolicy<a name="security-iam-AWSLicenseManagerUserSubscriptionsServiceRolePolicy"></a>

This policy is attached to the service\-linked role named `AWSServiceRoleAWSLicenseManagerUserSubscriptionsService` policy to allow License Manager to call API actions to manage user\-based subscription resources\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.

To view the permissions for this policy, see in the [AWSLicenseManagerUserSubscriptionsPolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSLicenseManagerUserSubscriptionsPolicy)\.

## License Manager updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for License Manager since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the License Manager Document history page\.


| Change | Description | Date | 
| --- | --- | --- | 
| [AWSLicenseManagerUserSubscriptionsServiceRolePolicy](#security-iam-AWSLicenseManagerMasterAccountRolePolicy) – Update to an existing policy | License Manager added the ec2:DescribeVpcPeeringConnections permission\. | November 28, 2022 | 
| [AWSLicenseManagerUserSubscriptionsServiceRolePolicy](#security-iam-AWSLicenseManagerMasterAccountRolePolicy) – New policy | License Manager added a permission to create the service\-linked role named AWSLicenseManagerUserSubscriptionsServiceRolePolicy\. This role provides License Manager permission to list AWS Directory Service resources, utilize Systems Manager features, and manage Amazon EC2 resources created for user\-based subscriptions\. | July 18, 2022 | 
| [AWSLicenseManagerMasterAccountRolePolicy](#security-iam-AWSLicenseManagerMasterAccountRolePolicy) – Update to an existing policy | License Manager added the resource\-groups:PutGroupPolicy permission for resource groups managed by AWS Resource Access Manager\. | June 27, 2022 | 
| [AWSLicenseManagerMasterAccountRolePolicy](#security-iam-AWSLicenseManagerMasterAccountRolePolicy) – Update to an existing policy | License Manager changed the AWS managed policy AWSLicenseManagerMasterAccountRolePolicy [condition key for AWS Resource Access Manager](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsresourceaccessmanager.html) from using ram:ResourceTag to aws:ResourceTag\. | November 16, 2021 | 
| [AWSLicenseManagerConsumptionPolicy](#security-iam-AWSLicenseManagerConsumptionPolicy) – New policy | License Manager added a new policy that grants permissions to consume licenses\. | August 11, 2021 | 
| [AWSLicenseManagerServiceRolePolicy](#security-iam-AWSLicenseManagerServiceRolePolicy) – Update to an existing policy | License Manager added a permission to list delegated administrators and a permission to create the service\-linked role named AWSServiceRoleForAWSLicenseManagerMemberAccountRole\. | June 16, 2021 | 
| [AWSLicenseManagerServiceRolePolicy](#security-iam-AWSLicenseManagerServiceRolePolicy) – Update to an existing policy | License Manager added a permission to list all License Manager resources, such as license configurations, licenses, and grants\. | June 15, 2021 | 
| [AWSLicenseManagerServiceRolePolicy](#security-iam-AWSLicenseManagerServiceRolePolicy) – Update to an existing policy | License Manager added a permission to create the service\-linked role named AWSServiceRoleForMarketplaceLicenseManagement\. This role provides AWS Marketplace with permissions to create and manage licenses in License Manager\. For more information, see [Service\-linked roles for AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-using-service-linked-roles.html) in the AWS Marketplace Buyer Guide\. | March 9, 2021 | 
| License Manager started tracking changes | License Manager started tracking changes to its AWS managed policies\. | March 9, 2021 | 