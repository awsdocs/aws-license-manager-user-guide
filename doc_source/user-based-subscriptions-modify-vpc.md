# Modifying VPC settings for user\-based subscriptions<a name="user-based-subscriptions-modify-vpc"></a>

If you added Microsoft Office products, you can modify the configuration for your VPC\. License Manager will create [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) on your behalf in the subnets you specify for your resources to reach the activation servers and remain in compliance\. You must specify at least one subnet\. For more information, see [Prerequisites](user-based-subscriptions-prerequisites.md)\.

**Note**  
VPC settings are only available to modify if your directory has been configured with Microsoft Office products\. For more information, see [Getting started with user\-based subscriptions](user-based-subscriptions-getting-started.md)\.  
If you want to remove all VPC endpoints, see [Considerations](user-based-subscriptions-considerations.md)\.

**To modify the directory configuration**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. On the Settings page, under the **Configured virtual private cloud** section, choose **Edit**\.

1. Change the subnets and security group as necessary for the configured VPC and then choose **Save changes**\.