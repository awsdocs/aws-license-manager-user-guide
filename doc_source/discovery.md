# Discover resource inventory<a name="discovery"></a>

License Manager uses [Systems Manager inventory](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html) to discover software usage on premises\. After you associate a license configuration with on\-premises servers, License Manager periodically collects software inventory, updates licensing information, and refreshes its dashboards to report usage\.

**Topics**
+ [Setting up for inventory search](#discovery-setup)
+ [Using inventory search](#using-discovery)
+ [Adding automated discovery rules to a license configuration](#add-discovery-rule)
+ [Associating a license configuration with discovered inventory](#discovered)
+ [Disassociating a license configuration and a resource](#disassociate)

## Setting up for inventory search<a name="discovery-setup"></a>

Complete the following requirements before using resource inventory search:
+ Enable cross\-account inventory discovery by integrating License Manager with your AWS Organizations account\. For more information, see [Settings in License Manager](settings.md)\.
+ Create license configurations for the servers and applications to manage\. For example, create a license configuration that reflects the terms of your licensing agreement with Microsoft for SQL Server Enterprise\.

## Using inventory search<a name="using-discovery"></a>

Complete the following steps to search your resource inventory\. You can search for applications by name \(for example, names that begin with "SQL Server"\) and the type of license included \(for example, a license that is not for "SQL Server Web"\)\.

**To search your resource inventory**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Search inventory**\.

1. Specify filter options to scope the list of displayed resources\.

   The following filters and logical operators are supported for Amazon EC2 resources:
   + **Resource ID** – The ID of the resource\. Logical operators are **Equals** and **Not equals**\.
   + **Account ID** – The ID of the AWS account that owns the resource\. Logical operators are **Equals** and **Not equals**\.
   + **Platform name** – The platform of the resource\. Logical operators are **Equals**, **Not equals**, **Begins with**, and **Contains**\.
   + **Application name** – The name of the application\. Logical operators are **Equals** and **Begins with**\.
   + **License included name** – The type of license included\. Logical operators are **Equals** and **Not equals**\. Possible values are **SQL Server Enterprise**, **SQL Server Standard**, **SQL Server Web**, and **Windows Server Datacenter**\.
   + **Tag** – The key/value combination of a tag assigned to the resource\. The tag value is optional\. Logical operators are **Equals** and **Not equals**\. **Not equals** is shown only if cross account discovery is enabled\.

   The following filters and logical operators are supported for Amazon RDS resources:
   + **Engine Edition**– The edition of the database engine\. Logical operator is **Equals**\. Possible values are: **Standard Edition**, **Standard Edition One**, **Standard Edition Two**, and **Enterprise Edition**\.
   + **License Pack**– The license pack\. Logical operator is **Equals**\. Possible values are: **Spatial and Graph**, **Active Data Guard**, **Label Security**, **Oracle On\-Line Analytical Processing \(OLAP\)**, and **Diagnostic Pack and Tuning Pack**\.

   For more information, see [Oracle Licensing](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Oracle.html#Oracle.Concepts.Licensing) in the *Amazon RDS User Guide*\.

## Adding automated discovery rules to a license configuration<a name="add-discovery-rule"></a>

After you add product information to your license configuration, License Manager can track license usage for the instances that have those products installed\. For more information, see [Automated discovery of resource inventory](automated-discovery.md)\.

**To add automated discovery rules to a license configuration**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Open the **Search inventory** page\.

1. Select the resource and choose **Add automated discovery rules**\.

1. For **License configuration**, select a license configuration\.

1. Specify the products to discover and track\.

1. \(Optional\) Select **Stop tracking instances when software is uninstalled** to make the license available for reuse after License Manager detects that the software was uninstalled and any license affinity period has elapsed\.

1. \(Optional\) To define resources to exclude from automated discovery select **Add exclusion rule**\.
**Note**  
Exclusion rules do not apply to RDS products \(such as Oracle Database\)\.

   1. Choose a **Property** to filter on, currently **Account ID**, and **Tag** are supported\.

   1. Enter the information to identify that property\. For an **Account ID** specify the 12 digit AWS Account ID as the value\. For **Tags** enter a key/value pair\.

   1. Repeat step 7 to add additional rules\.

1. Choose **Add**\.

## Associating a license configuration with discovered inventory<a name="discovered"></a>

After you have identified the unmanaged resources that you need to manage, you can manually associate them with a license configuration, instead of using automated discovery\.

**To associate a license configuration with a resource**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Open the **Search inventory** page\.

1. Select the resource and choose **Associate license configuration**\.

1. For **License configuration name**, select a license configuration\.

1. \(Optional\) Select **Share license configuration with all my member accounts**\.

1. Choose **Associate**\.

## Disassociating a license configuration and a resource<a name="disassociate"></a>

If the licensing terms from your software vendors change, you can disassociate resources that were associated manually and then delete the license configuration\.

**To disassociate a license configuration and a resource**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **License configuration**\.

1. Choose the name of the license configuration\.

1. Choose **Associated resources**\.

1. Select each of the resources to disassociate from the license configuration and then choose **Disassociate resource**\.