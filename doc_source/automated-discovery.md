# Automated discovery of inventory<a name="automated-discovery"></a>

License Manager uses [Systems Manager inventory](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html) to discover software usage on Amazon EC2 instances and on\-premises instances\. You can add product information to your self\-managed license, and License Manager will track the instances that have those products installed\. Additionally, you can specify exclusion rules based on your licensing agreement to decide which instances to exclude\. You can exclude instances belonging to AWS account IDs or associated with resource tags from being considered for automated discovery

Automated discovery can be added to a new license set, to an existing self\-managed license, or resources in your inventory\. Rules for automated discovery can be edited at any time through the CLI using the [UpdateLicenseConfiguration](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateLicenseConfiguration.html) API command\. To edit rules in the console, you must delete the existing self\-managed license and create a new one\.

To use automated discovery, you must add product information to your self\-managed license\. You can do so when you create the self\-managed license using **Inventory search**\.

You cannot manually disassociate instances tracked by automated discovery\. By default, automated discovery does not disassociate tracked instances after the software is uninstalled\. You can configure automated discovery to stop tracking instances when the software is uninstalled\.

After you configure automated discovery, you can track license usage through the License Manager dashboard\.

**Prerequisites**
+ Enable cross\-account inventory search by integrating License Manager with your AWS Organizations account\. For more information, see [Settings in License Manager](settings.md)\.
**Note**  
 Single accounts can set up automated discovery but cannot add exclusion rules\.
+ Install Systems Manager inventory on your instances\.

**To configure automated discovery when you create a self\-managed license**  
You can configure automated discovery rules and exclusion rules when you create a self\-managed license\. For more information, see [Create a self\-managed license](create-license-configuration.md)\.

**To add automated discovery rules to an existing self\-managed license**

 Use the process below to add automated discovery rules to existing self\-managed licenses through the console, you can also do this from the **Inventory search** pane by selecting an resource ID and selecting **Add automated discovery rules**\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Self\-managed licenses**\.

1. Choose the name of the self\-managed license to open the license details page\.

1. On the **Automated discovery rules** tab, choose **Add automated discovery rules**\.

1. Specify the products to discover and track\.

1. \(Optional\) Select **Stop tracking instances when software is uninstalled** to make the license available for reuse after License Manager detects that the software was uninstalled and any license affinity period has elapsed\.

1. \(Optional\) To define resources to exclude from automated discovery select **Add exclusion rule**\.
**Note**  
Exclusion rules do not apply to RDS products \(such as Oracle Database\)\.

   1. Choose a **Property** to filter on, currently **Account ID**, and **Tag** are supported\.

   1. Enter the information to identify that property\. For an **Account ID** specify the 12 digit AWS account ID as the value\. For **Tags** enter a key/value pair\.

   1. Repeat step 7 to add additional rules\.

1. When you are finished choose **Add** to apply your automated discovery rule\.