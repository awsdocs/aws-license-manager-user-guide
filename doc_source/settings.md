# Settings in License Manager<a name="settings"></a>

The **Settings** section of the License Manager console displays settings for the logged\-in account\. You must configure settings to enable certain functionality such as distribution of managed entitlements and self\-managed licenses to your organization, as well as for performing cross\-account inventory discovery\.

The settings for License Manager include the following:
+ **Account details**
+ **Cross\-account resource discovery**
+ **Delegated administrator**
+ **Microsoft Active Directory**
+ **Simple Notification Service \(SNS\)**

**To edit License Manager settings**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. Choose the relevant action for the setting you wish to configure or modify\. For example, you might choose **Edit** or **Turn on**\.

**Topics**
+ [Account details](#settings-account-details)
+ [Cross\-account resource discovery](#settings-resource-discovery)
+ [Delegated administrator](#settings-delegated-administrator)
+ [AWS Managed Microsoft AD](#settings-managed-ad)
+ [Virtual private cloud](#settings-vpc)
+ [Simple Notification Service \(SNS\)](#settings-sns)

## Account details<a name="settings-account-details"></a>

You can review your account details to see information such as the account type, whether accounts in AWS Organizations are linked, the account's License Manager S3 bucket ARN, and the AWS Resource Access Manager share ARN\. This section also enables you to link your AWS Organizations accounts\.

To distribute managed entitlements or self\-managed licenses within your organization, choose **Link AWS Organizations accounts**\. The distributed grants for managed entitlements are auto\-accepted by all of your member accounts\. When you select this option, we add a service\-linked role to the [ management](management-role.md) and [member](member-role.md) accounts\.

**Note**  
To enable this option, you must be signed in to your management account and all features must be enabled in AWS Organizations\. For more information, see [Enabling all features in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.  
 This selection also creates an AWS Resource Access Manager resource share in your management account, which allows you to seamlessly share self\-managed licenses\. For more information, see the [AWS Resource Access Manager User Guide](https://docs.aws.amazon.com/ram/latest/userguide)\. 

To disable this option, call the [UpdateServiceSettings](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateServiceSettings.html) API\.

## Cross\-account resource discovery<a name="settings-resource-discovery"></a>

You can turn on cross\-account resource discovery in order to manage license usage across all of your accounts in AWS Organizations\.

To enable cross\-account resource discovery in your organization, choose **Turn on** for cross\-account resource discovery\. When you turn on the cross\-account resource discovery, AWS Organizations will automatically be linked to perform resource discovery across all of your accounts\. 

**Note**  
License Manager uses [Systems Manager inventory](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html) to discover software usage\. Verify that you have configured Systems Manager inventory on all of your resources\. Querying Systems Manager inventory requires the following:  
[Resource data sync](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-inventory-datasync.html) to store inventory in an Amazon S3 bucket\.
[Amazon Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html) to aggregate inventory data from your accounts in AWS Organizations\.
[AWS Glue](https://docs.aws.amazon.com/glue) to provide a fast query experience\.

## Delegated administrator<a name="settings-delegated-administrator"></a>

You can delegate a member account from your organization to perform administrative tasks, such as sharing license configurations with other member accounts, performing cross\-account resource discovery, and distributing managed entitlements to other member accounts\. For more information, see [Register a delegated administrator](delegated-administrator.md)\.

## AWS Managed Microsoft AD<a name="settings-managed-ad"></a>

License Manager requires AWS Managed Microsoft AD to be configured before you can work with user\-based subscriptions\. For more information, see [User\-based subscriptions in AWS License Manager](user-based-subscriptions.md)\.

## Virtual private cloud<a name="settings-vpc"></a>

License Manager requires your VPC to be configured, in addition to your AWS Managed Microsoft AD, when you use user\-based subscriptions with Microsoft Office\. For more information, see [User\-based subscriptions in AWS License Manager](user-based-subscriptions.md)\.

## Simple Notification Service \(SNS\)<a name="settings-sns"></a>

You can configure an Amazon SNS to receive notifications and alerts from License Manager\.

**To configure an Amazon SNS topic**

1. Choose **Edit** next to **Simple Notification Service \(SNS\)**\.

1. Specify an SNS topic ARN in the following format:

   `arn:<aws_partition>:sns:region:account_id:aws-license-manager-service-*`

1. Choose **Save changes**\.