# License Manager–Management account role<a name="management-role"></a>

License Manager requires a service\-linked role to perform license management\.

## Permissions for the management account role<a name="service-linked-role-permissions-management-role"></a>

The service\-linked role named **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** allows License Manager access to AWS resources to manage license management actions for a central management account on your behalf\.

The **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** service\-linked role trusts the `license-manager.master-account.amazonaws.com` service to assume the role\.

The role permissions policy allows License Manager to complete the following actions on the specified resources\.


| Action | Resource ARN | 
| --- | --- | 
| s3:GetBucketLocation | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:ListBucket | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:GetLifecycleConfiguration | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:PutLifecycleConfiguration | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:GetBucketPolicy | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:PutBucketPolicy | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:AbortMultipartUpload | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:PutObject | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:GetObject | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:ListBucketMultipartUploads | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:ListMultipartUploadParts | arn:aws:s3:::aws\-license\-manager\-service\-\* | 
| s3:DeleteObject | arn:aws:s3:::aws\-license\-manager\-service\-\*/resource\-sync/\* | 
| athena:GetQueryExecution | \* | 
| athena:GetQueryResults | \* | 
| athena:StartQueryExecution | \* | 
| glue:GetTable | \* | 
| glue:GetPartition | \* | 
| glue:GetPartitions | \* | 
| organizations:DescribeOrganization | \* | 
| organizations:ListAccounts | \* | 
| organizations:DescribeAccount | \* | 
| organizations:ListChildren | \* | 
| organizations:ListParents | \* | 
| organizations:ListAccountsForParent | \* | 
| organizations:ListRoots | \* | 
| organizations:ListAWSServiceAccessForOrganization | \* | 
| ram:GetResourceShares | \* | 
| ram:GetResourceShareAssociations | \* | 
| ram:TagResource | \* | 
| ram:CreateResourceShare | \* | 
| ram:AssociateResourceShare | \* | 
| ram:DisassociateResourceShare | \* | 
| ram:UpdateResourceShare | \* | 
| ram:DeleteResourceShare | \* | 
| iam:GetRole | \* | 
| iam:PassRole | arn:aws:iam::\*:role/LicenseManagerServiceResourceDataSyncRole\* | 
| cloudformation:UpdateStack | arn:aws:cloudformation:\*:\*:stack/LicenseManagerCrossAccountCloudDiscoveryStack/\* | 
| cloudformation:CreateStack | arn:aws:cloudformation:\*:\*:stack/LicenseManagerCrossAccountCloudDiscoveryStack/\* | 
| cloudformation:DeleteStack | arn:aws:cloudformation:\*:\*:stack/LicenseManagerCrossAccountCloudDiscoveryStack/\* | 
| cloudformation:DescribeStacks | arn:aws:cloudformation:\*:\*:stack/LicenseManagerCrossAccountCloudDiscoveryStack/\* | 
| glue:CreateTable | See footnote † | 
| glue:UpdateTable | See footnote † | 
| glue:DeleteTable | See footnote † | 
| glue:UpdateJob | See footnote † | 
| glue:UpdateCrawler | See footnote † | 

† The following are the conditions for the AWS Glue actions:
+ `arn:aws:glue:*:*:catalog`
+ `arn:aws:glue:*:*:crawler/LicenseManagerResourceSynDataCrawler`
+ `arn:aws:glue:*:*:job/LicenseManagerResourceSynDataProcessJob`
+ `arn:aws:glue:*:*:table/license_manager_resource_inventory_db/*`
+ `arn:aws:glue:*:*:table/license_manager_resource_sync/*`
+ `arn:aws:glue:*:*:database/license_manager_resource_inventory_db`
+ `arn:aws:glue:*:*:database/license_manager_resource_sync`

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Create a management account service\-linked role<a name="create-service-linked-role-management"></a>

You don't need to manually create this service\-linked role\. When you configure cross\-account license management in the AWS Management Console, License Manager creates the service\-linked role for you\. 

**Note**  
To make use of cross\-account support in License Manager, you must be using AWS Organizations\.

If you delete this service\-linked role and then need to create it again, you can use the same process to re\-create the role in your account\.

You can also use the IAM console, AWS CLI, or IAM API to create a service\-linked role manually\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\.

**Important**  
This service\-linked role can appear in your account if you completed an action in another service that uses the features supported by this role\. If you were using License Manager before January 1, 2017, when it began supporting service\-linked roles, then License Manager created **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** in your account\. For more information, see [A New Role Appeared in My IAM Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

You can use the License Manager console to create this service\-linked role\. 

**To create the service\-linked role**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Settings**, **Edit**\.

1. Choose **Link AWS Organizations accounts**\.

1. Choose **Apply**\.

   

You can also use the IAM console to create a service\-linked role with the **License Manager**–Management account use case\. Alternatively, in the AWS CLI or the AWS API, use IAM to create a service\-linked role with the `license-manager.master-account.amazonaws.com` service name\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\. 

If you delete this service\-linked role, you can use the same IAM process to create the role again\.

## Edit a service\-linked role for License Manager<a name="edit-service-linked-role-management"></a>

License Manager does not allow you to edit the **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Delete a service\-linked role for License Manager<a name="delete-service-linked-role-management"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way, you only have entities that are actively monitored or maintained\. However, you must clean up your service\-linked role before you can manually delete it\.

### Manually delete the service\-linked role<a name="slr-manual-delete-management"></a>

Use the IAM console, AWS CLI, or AWS API to delete the **AWSServiceRoleForAWSLicenseManagerMasterAccountRole** service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.