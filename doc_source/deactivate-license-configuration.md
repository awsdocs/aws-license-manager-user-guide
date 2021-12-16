# Deactivate a license configuration<a name="deactivate-license-configuration"></a>

When you deactivate a license configuration, existing resources using the license are unaffected and AMIs using the license can still be launched\. However, license consumption is no longer tracked\.

When a license configuration is deactivated, it must not be attached to any running instance\. After deactivation, launches cannot be performed with the license configuration\.

**To deactivate a license configuration**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **License configurations**\.

1. Select the license configuration\.

1. Choose **Actions**, **Deactivate**\. When prompted for confirmation, choose **Deactivate**\.

**To deactivate a license configuration using the command line**
+ [update\-license\-configuration](https://docs.aws.amazon.com/cli/latest/reference/license-manager/update-license-configuration.html) \(AWS CLI\)
+ [Update\-LICMLicenseConfiguration](https://docs.aws.amazon.com/powershell/latest/reference/items/Update-LICMLicenseConfiguration.html) \(Tools for Windows PowerShell\)