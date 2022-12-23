# Monitoring AWS License Manager<a name="monitoring-overview"></a>

You can monitor the usage of licenses and subscriptions tracked in AWS License Manager using Amazon CloudWatch\. CloudWatch collects raw data and processes it into readable, near real\-time metrics\. You can set alarms that watch for certain thresholds, and send notifications or take actions when those thresholds are met\. For more information, see [Monitoring license usage with Amazon CloudWatch](monitoring-cloudwatch.md)\.

You can capture API calls and related events made by or on behalf of your AWS account using AWS CloudTrail\. Events are captured as log files and delivered to an Amazon S3 bucket that you specify\. You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred\. For more information, see [Logging AWS License Manager API calls using AWS CloudTrail](logging-using-cloudtrail.md)\.

**Contents**
+ [Monitoring license usage with Amazon CloudWatch](monitoring-cloudwatch.md)
  + [Creating alarms to monitor License Manager metrics](monitoring-cloudwatch.md#monitoring-cloudwatch-alarms)
+ [Logging AWS License Manager API calls using AWS CloudTrail](logging-using-cloudtrail.md)
  + [License Manager information in CloudTrail](logging-using-cloudtrail.md#license-manager-info-in-cloudtrail)
  + [Understanding License Manager log file entries](logging-using-cloudtrail.md#understanding-license-manager-entries)