# Usage metrics and Amazon CloudWatch alarms for Linux subscriptions<a name="linux-subscriptions-usage-alarms"></a>

The **Subscriptions** section of the AWS License Manager console lists the discovered commercial Linux subscriptions you have purchased on AWS or have brought in using the Bring Your Own Subscription model \(BYOS\)\. All commercial Linux subscriptions are on a per instance basis for licensing\.

The following details are available per discovered Linux subscription: 
+ Subscription name
+ Subscription type
+ Number of running instance per subscription
+ Configured Amazon CloudWatch alarms

When you choose a Linux subscription from the summary page, the **Usage metrics and alarms** tab will display data for that subscription\. In this tab, Amazon CloudWatch dashboards display for the chosen subscription within the License Manager console\. You can adjust the dashboard to encompass a certain time frame, or *evaluation range,* in hours, days, or a week from a selected date\.

In the **Usage metrics and alarms** tab, each subscription has an **Alarms** section which details the following:
+ **Alarm name** – The name of the alarm\.
+ **State** – The state of the alarm\.
+ **Dimension** – The dimensions of the alarm\. The dimension will include the Region and instance type that was defined\.
+ **Condition** – The condition of the alarm\. The condition will include the comparison operator and alarm threshold value that was defined\.

You can create CloudWatch alarms using the dimensions and conditions you define to track and alert based on your current subscription utilization\. The Linux subscriptions console displays a summary of the subscription names in use, the subscription types, amount of running instances for each, and the alarm status\.

The following are possible CloudWatch alarm states:
+ **OK** – The metric or expression is within the defined threshold\.
+ **ALARM** – The metric or expression is outside of the defined threshold\.
+ **INSUFFICIENT\_DATA** – The alarm has just started, the metric is not available, or not enough data is available for the metric to determine the alarm state\.

**Topics**
+ [Creating an alarm for Linux subscriptions](#linux-subscriptions-alarms-create)
+ [Modifying an alarm for Linux subscriptions](#linux-subscriptions-alarms-modify)
+ [Deleting an alarm for Linux subscriptions](#linux-subscriptions-alarms-delete)

## Creating an alarm for Linux subscriptions<a name="linux-subscriptions-alarms-create"></a>

You can create alarms for each commercial Linux subscription that you have discovered on your running EC2 instances\. If necessary, you can create multiple alarms with different dimensions and conditions for each subscription\.

**To create a CloudWatch alarm for Linux subscriptions using the console**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under Linux subscriptions, choose **Subscriptions**\.

1. Under the **Subscription name** column, choose the subscription to create an alarm for, then choose **Create alarm**\.

1. Specify the following for the alarm: 
   + **Alarm name** – specify a name which resembles `AWS-LM-LS-AlarmName`\.
   + Instance type – choose an instance type that will be using the subscription that was selected\.
   + Usage Region – choose the Regions to create the alarms for\.
   + Comparison operator – the comparison operator for the alarm threshold\.
   + Alarm threshold value – the value for the alarm threshold\.

1. Choose **Create** to create the alarm\. 

## Modifying an alarm for Linux subscriptions<a name="linux-subscriptions-alarms-modify"></a>

You can modify existing alarms to adapt to changing requirements from the License Manager console\.

**To modify a CloudWatch alarm for Linux subscriptions using the console**Modifying an alarm

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under Linux subscriptions, choose **Subscriptions**\.

1. Under the **Subscription name** column, choose the subscription to modify, then choose **Edit**\.

1. Modify the defined values as required\.

1. Choose **Edit** to modify the alarm\.

## Deleting an alarm for Linux subscriptions<a name="linux-subscriptions-alarms-delete"></a>

You can delete existing alarms to adapt to changing requirements from the License Manager console\.

**To delete a CloudWatch alarm for Linux subscriptions using the console**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under Linux subscriptions, choose **Subscriptions**\.

1. Under the **Subscription name** column, choose the subscription to modify, then choose **Delete**\.