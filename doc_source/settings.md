# Settings in License Manager<a name="settings"></a>

The **Settings** section of the License Manager console displays settings for the logged\-in account\. You must configure settings to enable distribution of managed entitlements and license configurations to your organization, as well as for performing cross\-account inventory discovery\.

The settings for License Manager include the following:
+ **Account type**
+ **S3 bucket ARN**
+ **Link AWS Organizations account** status
+ **SNS topic ARN**
+ **Cross\-account resource discovery**
+ **Resource share ARN**
+ **Register/De\-register Delegated Admin** \(if applicable\)

**To edit License Manager settings**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. Choose **Edit**\.

**Enable distribution of managed entitlements or license configurations to your organization**  
To distribute managed entitlements or license configurations within your organization, select the check box next to **Link AWS Organizations accounts**\. The distributed grants for managed entitlements are auto\-accepted by all of your member accounts\. When you select this option, we add a service\-linked role to the [ management](management-role.md) and [member](member-role.md) accounts\.

**Note**  
To enable this option, you must be signed in to your management account and all features must be enabled in AWS Organizations\. For more information, see [Enabling all features in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.  
 This selection also creates an AWS Resource Access Manager resource share in your management account, which allows you to seamlessly share license configurations\. For more information, see the [AWS Resource Access Manager User Guide](https://docs.aws.amazon.com/ram/latest/userguide)\. 

To disable this option, call the [UpdateServiceSettings](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateServiceSettings.html) API\. 

**Perform cross\-account resource discovery in your AWS Organizations**  
To enable cross\-account resource discovery in your Organizations, select the check box next to **Turn on cross\-account inventory search**\. When you turn on the cross\-account inventory search, your AWS Organizations will automatically be linked to perform inventory search across all of your accounts\. 

**Note**  
License Manager uses [Systems Manager inventory](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html) to discover software usage\. Verify that you have configured Systems Manager inventory on all of your resources\. Querying Systems Manager inventory requires the following:  
[Resource data sync](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-inventory-datasync.html) to store inventory in an Amazon S3 bucket\.
[Amazon Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html) to aggregate inventory data from organizational accounts\.
[AWS Glue](https://docs.aws.amazon.com/glue) to provide a fast query experience\.

 \(Optional\) For Amazon Simple Notification Service, edit the **Amazon SNS topic ARN**\. The ARN must use the following format:

`arn:<aws_partition>:sns:region:account_id:aws-license-manager-service-*`