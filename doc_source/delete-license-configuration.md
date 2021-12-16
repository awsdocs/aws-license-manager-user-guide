# Delete a license configuration<a name="delete-license-configuration"></a>

Before you can delete a license configuration, you must disassociate any resources\. You can delete a license configuration if you need to start over with new licensing rules\. If the licensing terms from your software vendors change, you can disassociate existing resources, delete the license configuration, create a new license configuration to reflect the updated terms and associate it with the existing resources\.

**To delete a license configuration using the console**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Customer managed licenses**\.

1. Choose the name of the license configuration to open the license details page\.

1. Select each resource \(individually or in bulk\) and choose **Disassociate resource**\. Repeat until the list is empty\.

1. Choose **Actions**, **Delete**\. When prompted for confirmation, choose **Delete**\.

**To delete a license configuration using the command line**
+ [delete\-license\-configuration](https://docs.aws.amazon.com/cli/latest/reference/license-manager/delete-license-configuration.html) \(AWS CLI\)
+ [Remove\-LICMLicenseConfiguration](https://docs.aws.amazon.com/powershell/latest/reference/items/Remove-LICMLicenseConfiguration.html) \(Tools for Windows PowerShell\)