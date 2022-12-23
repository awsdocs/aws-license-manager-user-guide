# Managing discovery of Linux subscriptions<a name="linux-subscriptions-manage-discovery"></a>

You can manage the discovery of Linux subscriptions using the License Manager console\. When you enable discovery of Linux subscriptions for the AWS Regions you specify, you can optionally extend this discovery to your accounts in AWS Organizations\. If you no longer want to track subscription utilization, you can also disable discovery\.

**Note**  
You can discover and display up to 5,000 resources per account per AWS Region by default\. To request an increase to these limits, use the [limit increase form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase)\.

**Topics**
+ [Enabling discovery of Linux subscriptions](#linux-subscriptions-enable-discovery)
+ [Resource discovery status reasons](#linux-subscriptions-status-reasons)
+ [Disabling discovery of Linux subscriptions](#linux-subscriptions-disable-discovery)

## Enabling discovery of Linux subscriptions<a name="linux-subscriptions-enable-discovery"></a>

To enable the discovery of Linux subscriptions, you need to configure the required settings in License Manager\. From the settings page, you can create the service\-linked role, specify which AWS Regions to enable discovery in, and whether to discover resources across your accounts in AWS Organizations\.

**To enable discovery for Linux subscriptions**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. On the **Settings** page, choose the **Linux subscriptions** tab and choose **Configure**\.

1. For **Source AWS Regions**, choose the Regions for which you want to discover Linux subscriptions\.

1. If you want to aggregate subscription data across your accounts in AWS Organizations, select **Link AWS Organizations**\.

1. Review and acknowledge the option which grants AWS License Manager permission to create a service\-linked role for Linux subscriptions\.

1. Choose **Save configuration**\.

## Resource discovery status reasons<a name="linux-subscriptions-status-reasons"></a>

 AWS License Manager will display a status and a corresponding status reason for each AWS Region you choose to enable discovery for Linux subscriptions\. The status reason will vary if you have linked Linux subscriptions with AWS Organizations: 
+ In progress
+ Successful
+ Failed

The status reason that displays for each Region you choose will show up to two status reasons at a time\. The following table provides more detail:


| Status reason action | Description | 
| --- | --- | 
|  Account\-onboard  | Onboarding a single account\. | 
|  Account\-offboard  | Offboarding a single account\. | 
|  Org\-onboard  | Onboarding an entire organization\. | 
|  Org\-offboard  | Offboarding an entire organization\. | 

You can call the `UpdateServiceSettings` API and subsequently call the `GetServiceSettings` API to monitor the progress of enabling Linux subscriptions\. Each status and status reason can apply to multiple Regions at once\. The follow table provides more detail on the status and status reason:

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/license-manager/latest/userguide/linux-subscriptions-manage-discovery.html)

## Disabling discovery of Linux subscriptions<a name="linux-subscriptions-disable-discovery"></a>

You can disable discovery of Linux subscriptions from the AWS License Manager settings page\.

**Warning**  
If you disable discovery, all of your data previously discovered for Linux subscriptions will be removed from AWS License Manager\.

**To disable discovery for Linux subscriptions**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. On the **Settings** page, choose the **Linux subscriptions** tab and choose **Disable Linux subscription discovery**\.

1. Type **Disable** and then choose **Disable** to confirm deactivation\.

1. \(Optional\) Remove the service\-linked role used for Linux subscriptions\. For more information, see [Delete a service\-linked role for License Manager](https://docs.aws.amazon.com/ license-manager/latest/userguide/linux-subscriptions-role.html)\.

1. \(Optional\) Disable trusted access between License Manager and your organization\. For more information, see [AWS License Manager and AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-license-manager.html)\.