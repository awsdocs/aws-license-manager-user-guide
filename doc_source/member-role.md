# License Manager – Member account role<a name="member-role"></a>

License Manager requires a service\-linked role that allows the management account to manage licenses\.

## Permissions for the member account role<a name="service-linked-role-permissions-member"></a>

The service\-linked role named `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` allows License Manager to access AWS resources for license management actions from a configured management account on your behalf\.

The `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` service\-linked role trusts the `license-manager.member-account.amazonaws.com` service to assume the role\.

The role permissions policy allows License Manager to complete the following actions on the specified resources\.


| Action | Resource ARN | 
| --- | --- | 
| license\-manager:UpdateLicenseSpecificationsForResource | \* | 
| license\-manager:GetLicenseConfiguration | \* | 
| ssm:ListInventoryEntries | \* | 
| ssm:GetInventory | \* | 
| ssm:CreateAssociation | \* | 
| ssm:CreateResourceDataSync | \* | 
| ssm:DeleteResourceDataSync | \* | 
| ssm:ListResourceDataSync | \* | 
| ssm:ListAssociations | \* | 
| ram:AcceptResourceShareInvitation | \* | 
| ram:GetResourceShareInvitations | \* | 

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Create the service\-linked role for License Manager<a name="create-service-linked-role-member"></a>

You don't need to manually create the service\-linked role\. You can enable integration with AWS Organizations from the management account in the License Manager console on the **Settings** page\. You can also do this using the AWS CLI \(run `update-service-settings`\) or the AWS API \(call `UpdateServiceSettings`\)\. When you do, License Manager creates the service\-linked role for you in the Organizations member accounts\.

If you delete this service\-linked role and then need to create it again, you can use the same process to recreate the role in your account\.

You can also use the IAM console, AWS CLI, or the IAM API to create a service\-linked role manually\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\.

**Important**  
This service\-linked role can appear in your account if you completed an action in another service that uses the features supported by this role\. If you were using the License Manager service before January 1, 2017, when it began supporting service\-linked roles, then License Manager created the `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` role in your account\. For more information, see [A New Role Appeared in My IAM Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

You can use the License Manager console to create a service\-linked role\.

**To create the service\-linked role**

1. Log in to your AWS Organizations management account\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**, and then choose **Edit**\.

1. Choose **Link AWS Organizations accounts**\.

1. Choose **Apply**\. This creates the roles [AWSServiceRoleForAWSLicenseManagerRole](license-manager-role-core.md) and [AWSServiceRoleForAWSLicenseManagerMemberAccountRole](#member-role) in all child accounts\.

You can also use the IAM console to create a service\-linked role with the **License Manager \- Member account** use case\. Alternatively, in the AWS CLI or AWS API, create a service\-linked role with the `license-manager.member-account.amazonaws.com` service name\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\. 

If you delete this service\-linked role, you can use the same IAM process to create the role again\.

## Edit a service\-linked role for License Manager<a name="edit-service-linked-role-member"></a>

License Manager does not allow you to edit the `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Delete a service\-linked role for License Manager<a name="delete-service-linked-role-member"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way, you only have entities that are actively monitored or maintained\. However, you must clean up your service\-linked role before you can manually delete it\.

### Manually delete the service\-linked role<a name="slr-manual-delete-member"></a>

Use the IAM console, AWS CLI, or AWS API to delete the `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.