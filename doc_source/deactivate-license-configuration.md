# Deactivate a self\-managed license<a name="deactivate-license-configuration"></a>

When you deactivate a self\-managed license, existing resources using the license are unaffected and AMIs using the license can still be launched\. However, license consumption is no longer tracked\.

When a self\-managed license is deactivated, it must not be attached to any running instance\. After deactivation, launches cannot be performed with the self\-managed license\.

**To deactivate a self\-managed license**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **self\-managed licenses**\.

1. Select the self\-managed license\.

1. Choose **Actions**, **Deactivate**\. When prompted for confirmation, choose **Deactivate**\.

**To deactivate a self\-managed license using the command line**
+ [update\-license\-configuration](https://docs.aws.amazon.com/cli/latest/reference/license-manager/update-license-configuration.html) \(AWS CLI\)
+ [Update\-LICMLicenseConfiguration](https://docs.aws.amazon.com/powershell/latest/reference/items/Update-LICMLicenseConfiguration.html) \(Tools for Windows PowerShell\)