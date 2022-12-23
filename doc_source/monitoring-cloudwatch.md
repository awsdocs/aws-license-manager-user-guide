# Monitoring license usage with Amazon CloudWatch<a name="monitoring-cloudwatch"></a>

You can monitor metric statistics for License Manager using Amazon CloudWatch\. These statistics are kept for 15 months, so that you can access historical information and gain a better perspective on how your web application or service is performing\. You can set alarms that watch for certain thresholds and send notifications or take actions when those thresholds are met\. For example, you can watch for the percentage of licenses using the `LicenseConfigurationUsagePercentage` metric, and take action before limits are exceeded\. For more information, see the [Amazon CloudWatch User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.

License Manager emits the following metrics hourly in the `AWSLicenseManager/licenseUsage` namespace:


| Metric | Description | 
| --- | --- | 
| RunningInstancesCount |  The total number of instances running in the current account that are grouped by the subscription name\. Units: Count Dimensions: `SubscriptionName`: The name of the subscription\.  | 
| AggregateRunningInstancesCount |  The aggregated total number of instances that are running across all of your accounts in AWS Organizations in the current AWS Region\.Units: CountDimensions: `SubscriptionName`: The name of the subscription\. | 
| TotalLicenseConfigurationUsageCount | The total number of a license configuration that could be available\. Units: CountDimensions:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/license-manager/latest/userguide/monitoring-cloudwatch.html)  | 
|  LicenseConfigurationUsageCount  | The total number of used licenses of this configuration\.Units: CountDimensions:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/license-manager/latest/userguide/monitoring-cloudwatch.html)  | 
| LicenseConfigurationUsagePercentage |  The used licenses of this license configuration expressed as a percentage\. Units: Percent Dimensions: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/license-manager/latest/userguide/monitoring-cloudwatch.html)  | 

## Creating alarms to monitor License Manager metrics<a name="monitoring-cloudwatch-alarms"></a>

You can create a CloudWatch alarm that sends an Amazon Simple Notification Service \(Amazon SNS\) message when the value of the metric changes and causes the alarm to change state\. An alarm watches a metric over a time period you specify, and performs actions based on the value of the metric relative to a given threshold over a number of time periods\. Alarms invoke actions for sustained state changes only\. CloudWatch alarms do not invoke actions simply because they are in a particular state; the state must have changed and been maintained for a specified number of periods\. For more information, see [Using CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)\.