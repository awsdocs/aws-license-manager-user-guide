# Viewing discovered instance data<a name="linux-subscriptions-instances-view"></a>

Once the initial resource discovery has completed, you will be able to view your Linux subscriptions discovered in the AWS Regions you selected\. If you chose to link AWS Organizations, data from accounts across your organization will be aggregated as well\. You can navigate to the **Instances** section of the AWS License Manager console to view a table of the data\. You can navigate to the **Instances** section of the AWS License Manager console to view a table of the data\.

Data for each instance includes the following:
+ **Instance ID** – The ID of the instance\.
+ **Instance type** – The type of instance\.
+ **Account ID** – The ID of the account which owns the instance\.
+ **Status** – The status of the instance\.
+ **Region** – The AWS Region in which the instance resides\.
+ **Usage operation** – The operation of the instance and the billing code that is associated with the AMI\. For more information, see [Usage operation values](conversion-types.md#usage-operation-values)\.
+ **Product code** – The product code associated with the AMI used to launch the instance\. For more information, see [AMI product codes](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes)\.
+ **AMI ID** – The ID of the AMI used to launch the instance\.

**Topics**
+ [Viewing data for all instances](#linux-subscriptions-instances-view-all)
+ [Viewing data for instances per subscription](#linux-subscriptions-instances-view-subscription)

## Viewing data for all instances<a name="linux-subscriptions-instances-view-all"></a>

You can view data for all instances has been aggregated across accounts in your organization within the chosen Regions\.

**To view discovered data for all of your instances**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under Linux subscriptions, choose **Instances**\.

1. Review the data as needed in the console\. You can filter the data by:
   + Instance ID
   + Account
   + Region
   + AMI ID
   + Usage operation
   + Product code

1. \(Optional\) Choose **Export view to CSV** to export data for all of your instances as a comma\-separated values file \(CSV\)\.

## Viewing data for instances per subscription<a name="linux-subscriptions-instances-view-subscription"></a>

You can view data for all instances has have been aggregated across accounts in your organization within the chosen Regions\.

**To view discovered data for instances with a specific subscription**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under Linux subscriptions, choose **Subscriptions**\.

1. Under the **Subscription name** column, choose the subscription you would like to view data for\.

1. Choose the **Instances** tab and review the data as needed in the console\. You can filter the data by:
   + Instance ID
   + Account
   + Region
   + AMI ID
   + Usage operation
   + Product code

1. \(Optional\) Choose **Export view to CSV** to export data for your instances with this subscription as a comma\-separated values file \(CSV\)\.