# Modifying directory settings for user\-based subscriptions<a name="user-based-subscriptions-modify-ad"></a>

You can add or remove products for user\-based subscriptions from your configured directory in the License Manager settings page\. The steps will differ if you are using Microsoft Office products because License Manager must create [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) for these subscriptions\.

**To modify the directory configuration without Microsoft Office products**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Settings**\.

1. On the Settings page, under the **AWS Managed Microsoft AD** section, choose **Edit**\.

1. For **Product Name and ID**, select additional products and clear previous selections as necessary and then choose **Save changes**\.

**To modify the directory configuration with Microsoft Office products**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Navigate to the **Settings** page by choosing **Settings** in the left navigation pane, or by choosing **Open Settings** in the banner\.

1. On the **Settings** page, under the **AWS Managed Microsoft AD** section, choose **Edit**\.

1. For **Product Name and ID**, select any required products, including Microsoft Office\.

1. For **Virtual private cloud**, choose a VPC for additional configuration\.

1. For **Subnets for vpc\-*x***, choose at least one subnet in which to provision VPC endpoints\.

1. For **Security groups for vpc\-*x***, choose the security group you created to associate with the VPC endpoints and then choose **Save changes**\.

   After you choose **Save changes**, the **AWS Managed Microsoft AD** and **Virtual private cloud** sections on the **Settings **page will display your **Directory ID** and **VPC ID** with the **Status **of **Configuring**\. You must wait until the directory has a **Status** of **Configured** and the VPC has a **Status **of **Active** before using user\-based subscriptions with Microsoft Office\.