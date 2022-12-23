# Linux subscriptions in AWS License Manager<a name="linux-subscriptions"></a>

AWS License Manager provides you with the capability to view and manage commercial Linux subscriptions which you own and run on AWS\. License utilization can be tracked across AWS Regions and accounts in AWS Organizations\. Once data is discovered and aggregated, you will have insight to all your instances using commercial Linux subscriptions\. In addition, your discovered subscription data will be displayed in the License Manager console as Amazon CloudWatch dashboards\.

You track utilization across multiple subscriptions such as:
+ Red Hat Enterprise Linux \(RHEL\) subscription\-included
+ RHEL Bring Your Own Subscription model \(BYOS\) with the Red Hat Cloud Access Program
+ SUSE Linux Enterprise Server
+ Ubuntu Pro

Linux subscriptions uses the eventual consistency model\. A consistency model determines the manner and timing in which data is loaded and presented in your Linux subscriptions view\. With this model, License Manager ensures that your Linux subscription data will be updated periodically from your resources\. In the event that some data is not ingested during these intervals, the information will be delivered at the next metric emission\. This behavior can delay resources, such as newly launched EC2 commercial Linux instances, from displaying in the Linux subscriptions dashboard\.

**Note**  
It can take up to 36 hours for the initial resource discovery to complete, and up to 12 hours for newly launched instances to be discovered and reported\. Once your resources are discovered, Amazon CloudWatch metrics are emitted hourly for Linux subscriptions data\.

**Contents**
+ [Managing discovery of Linux subscriptions](linux-subscriptions-manage-discovery.md)
  + [Enabling discovery of Linux subscriptions](linux-subscriptions-manage-discovery.md#linux-subscriptions-enable-discovery)
  + [Resource discovery status reasons](linux-subscriptions-manage-discovery.md#linux-subscriptions-status-reasons)
  + [Disabling discovery of Linux subscriptions](linux-subscriptions-manage-discovery.md#linux-subscriptions-disable-discovery)
+ [Viewing discovered instance data](linux-subscriptions-instances-view.md)
  + [Viewing data for all instances](linux-subscriptions-instances-view.md#linux-subscriptions-instances-view-all)
  + [Viewing data for instances per subscription](linux-subscriptions-instances-view.md#linux-subscriptions-instances-view-subscription)
+ [Billing information for Linux subscriptions](linux-subscriptions-billing-information.md)
+ [Usage metrics and Amazon CloudWatch alarms for Linux subscriptions](linux-subscriptions-usage-alarms.md)
  + [Creating an alarm for Linux subscriptions](linux-subscriptions-usage-alarms.md#linux-subscriptions-alarms-create)
  + [Modifying an alarm for Linux subscriptions](linux-subscriptions-usage-alarms.md#linux-subscriptions-alarms-modify)
  + [Deleting an alarm for Linux subscriptions](linux-subscriptions-usage-alarms.md#linux-subscriptions-alarms-delete)