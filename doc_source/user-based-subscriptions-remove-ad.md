# Removing a directory for user\-based subscriptions<a name="user-based-subscriptions-remove-ad"></a>

You can remove your directory if you no longer want to use it for user\-based subscriptions\. Removing the directory’s configuration from License Manager does not delete the directory itself\. When you remove the directory, you can't associate users from the directory for user\-based subscriptions\.

**Important**  
You must first disassociate users and terminate instances providing user\-based subscriptions before you can remove the directory from License Manager\.

**To remove a directory**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. On the **Settings** page, under the AWS Managed Microsoft AD section, choose **Remove**\.

1. Enter the required text to confirm you want to remove the directory and choose **Remove**\.

After you choose **Remove**, the **AWS Managed Microsoft AD** section on the **Settings** page will display your **Directory ID** with the **Status** of **Configuring**\. Once the configuration process is complete, the directory should be removed from the **AWS Managed Microsoft AD** section\.