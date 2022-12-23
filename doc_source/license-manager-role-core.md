# License Manager – Core role<a name="license-manager-role-core"></a>

License Manager requires a service\-linked role to manage licenses on your behalf\.

## Permissions for the core role<a name="service-linked-role-permissions-core-role"></a>

The service\-linked role named `AWSServiceRoleForAWSLicenseManagerRole` allows License Manager access to AWS resources to manage licenses on your behalf\.

The `AWSServiceRoleForAWSLicenseManagerRole` service\-linked role trusts the `license-manager.amazonaws.com` service to assume the role\.

The role permissions policy allows License Manager to complete the following actions on the specified resources\.


| Action | Resource ARN | 
| --- | --- | 
| iam:CreateServiceLinkedRole | arn:aws:iam::\*:role/aws\-service\-role/license\-management\.marketplace\.amazonaws\.com/AWSServiceRoleForMarketplaceLicenseManagement | 
| iam:CreateServiceLinkedRole | arn:aws:iam::\*:role/aws\-service\-role/license\-manager\.member\-account\.amazonaws\.com/AWSServiceRoleForAWSLicenseManagerMemberAccountRole | 
| s3:GetBucketLocation | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:ListBucket | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:ListAllMyBuckets | \* | 
| s3:PutObject | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| sns:Publish | arn:aws::sns:\*:\*:aws\-license\-manager\-service\-\* | 
| sns:ListTopics | \* | 
| ec2:DescribeInstances | \* | 
| ec2:DescribeImages | \* | 
| ec2:DescribeHosts | \* | 
| ssm:ListInventoryEntries | \* | 
| ssm:GetInventory | \* | 
| ssm:CreateAssociation | \* | 
| organizations:ListAWSServiceAccessForOrganization | \* | 
| organizations:DescribeOrganization | \* | 
| organizations:ListDelegatedAdministrators | \* | 
| license\-manager:GetServiceSettings | \* | 
| license\-manager:GetLicense\* | \* | 
| license\-manager:UpdateLicenseSpecificationsForResource | \* | 
| license\-manager:List\* | \* | 

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Create a service\-linked role for License Manager<a name="create-service-linked-role-core"></a>

You don't need to manually create a service\-linked role\. When you complete the License Manager first\-run experience form the first time that you visit the License Manager console, the service\-linked role is automatically created for you\. 

You can also use the IAM console, AWS CLI, or IAM API to create a service\-linked role manually\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\. 

**Important**  
This service\-linked role can appear in your account if you completed an action in another service that uses the features supported by this role\. If you were using License Manager before January 1, 2017, when it began supporting service\-linked roles, then License Manager created the `AWSServiceRoleForAWSLicenseManagerRole` role in your account\. For more information, see [A New Role Appeared in My IAM Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

You can use the License Manager console to create a service\-linked role\.

**To create the service\-linked role**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Start using License Manager**\.

1. In the **IAM Permissions \(one\-time\-setup\)** form, select **I grant AWS License Manager the required permissions**, then choose **Continue**\.

You can also use the IAM console to create a service\-linked role with the **License Manager** use case\. Alternatively, in the AWS CLI or the AWS API, use IAM to create a service\-linked role with the `license-manager.amazonaws.com` service name\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\. 

If you delete this service\-linked role, you can use the same IAM process to create the role again\.

## Edit a service\-linked role for License Manager<a name="edit-service-linked-role-core"></a>

License Manager doesn't allow you to edit the `AWSServiceRoleForAWSLicenseManagerRole` service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Delete a service\-linked role for License Manager<a name="delete-service-linked-role-core"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way, you only have entities that are actively monitored or maintained\. However, you must clean up your service\-linked role before you can manually delete it\.

### Clean up a service\-linked role<a name="service-linked-role-review-before-delete-core"></a>

Before you can use IAM to delete a service\-linked role, you must first delete all resources used by the role\. This means disassociating any self\-managed licenses from associated instances and AMIs, and then deleting the self\-managed licenses\.

**Note**  
If License Manager is using the role when you try to delete the resources, then the deletion might fail\. If that happens, wait for a few minutes and try the action again\.

**To delete License Manager resources used by the core role**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Self\-managed licenses**\.

1. Choose a self\-managed license for which you are the owner and disassociate all entries within the **Associated AMIs** and **Resources** tabs\. Repeat this process for each license configuration\.

1. While still on the self\-managed license's page, choose **Actions**, then choose **Delete**\.

1. Repeat the previous steps until all self\-managed licenses have been deleted\.

### Manually delete the service\-linked role<a name="slr-manual-delete-core"></a>

Use the IAM console, the AWS CLI, or the AWS API to delete the `AWSServiceRoleForAWSLicenseManagerRole` service\-linked role\. If you are also using [AWSLicenseManagerMasterAccountRole](management-role.md) and [AWSLicenseManagerMemberAccountRole](member-role.md), delete those roles first\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\. 