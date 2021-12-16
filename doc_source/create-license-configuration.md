# Create a license configuration<a name="create-license-configuration"></a>

A license configuration represents the licensing terms in the agreement with your software vendor\. Your license configuration specifies how your licenses should be counted \(for example, by vCPUs or number of instances\)\. It also specifies limits on your usage, so that you can prevent usage from going over the number of allocated licenses\. Additionally, it can also specify other constraints on your licenses, such as the tenancy type\.

**Requirements for Oracle Database products**

When you add product information to configure automated discovery of Oracle Database products, the following requirements apply:
+ The supported license counting type is `vCPU`\.
+ Rules are not supported\.
+ Hard license limits are not supported\.
+ You can track one product version per license configuration\.
+ You cannot track Oracle products and other products using the same license configuration\.

**To create a license configuration using the console**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **License configurations**\.

1. Choose **Create license configuration**\.

1. In the **Configuration details** panel, provide the following information:
   + **License configuration name** — A name for the license configuration\.
   + **Description** — An optional description of the license configuration\.
   + **License type** — The counting model for this license \(**vCPUs**, **Cores**, **Sockets**, or **Instances**\)\.
   + **Number of <option>** — The option displayed depends on the license type\. When the license limit is exceeded, License Manager notifies you \(soft limit\) or prevents a resource from deploying \(hard limit\)\.
   + **Enforce license limit** — If selected, the license limit is a hard limit\.
   + **Rules** — One or more rules\. For each rule, select a rule type, provide a rule value, and choose **Add rule**\. The rule types displayed depend on the license type\. For example, minimum values, maximum values, and tenancy\. If you do not specify a tenancy type, all are accepted\.

1. \(Optional\) In the **Automated discovery rules** panel, do the following:

   1. Choose the product name, product type, and resource type for each product to discover and track using [automated discovery](automated-discovery.md)\.

   1. Select **Stop tracking instances when software is uninstalled** to make the license available for reuse after License Manager detects that the software was uninstalled and any license affinity period has elapsed\.

   1. \(Optional\) If your account is a License Manager management account for an Organizations you have to option to define resources to exclude from automated discovery\. To do so select **Add exclusion rule**, choose the property to filter on, AWS account IDs and resource Tags are supported, then enter the information to identify that property\.

1. \(Optional\) Expand the **Tags** panel to add one or more tags to your license configuration\. Tags are key/value pairs\. Provide the following information for each tag:
   + **Key** — The searchable name of the key\.
   + **Value** — The value for the key\.

1. Choose **Submit**\.

**To create a license configuration using the command line**
+ [create\-license\-configuration](https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-license-configuration.html) \(AWS CLI\)
+ [New\-LICMLicenseConfiguration](https://docs.aws.amazon.com/powershell/latest/reference/items/New-LICMLicenseConfiguration.html) \(Tools for Windows PowerShell\)