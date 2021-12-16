# Working with AWS License Manager<a name="using-license-manager"></a>

License Manager can be applied to standard scenarios for enterprises with a mixed infrastructure of AWS resources and on\-premises resources\. You can create license configurations, take inventory of your license\-consuming resources, associate licenses with resources, and track inventory and compliance\.

**Licensing for AWS Marketplace products**  
Using License Manager, you can now associate licensing rules to AWS Marketplace BYOL AMI products via Amazon EC2 launch templates, AWS CloudFormation templates, or AWS Service Catalog products\. In each case, you benefit from centralized license\-tracking and compliance enforcement\.

**Note**  
License Manager does not change how you obtain and activate your BYOL AMIs from Marketplace\. After launching, you must provide a license key obtained directly from the seller to activate any third\-party software\.

**Tracking licenses for resources in on\-premises data centers**  
With License Manager, you can discover applications running outside of AWS with the [Systems Manager inventory](http://aws.amazon.com/systems-manager/faq/), and then attach licensing rules to them\. After licensing rules are attached, you can track on\-premises servers along with AWS resources in the License Manager console\.

**Differentiate between license included and BYOL**  
With License Manager, you can identify which resources have a license that is included with the product and which use a license that you own\. This enables you to accurately report how you are using BYOL licenses\. This filter requires SSM version 2\.3\.722\.0 or later\.<a name="cross-account-support"></a>

**License Manager across your AWS accounts**

License Manager enables you to manage licenses across your AWS accounts\. You can create license configurations once in your AWS Organizations management account and share them across your accounts using AWS Resource Access Manager or by linking AWS Organizations accounts using License Manager settings\. This also enables you to perform cross\-account discovery to search inventory across your AWS accounts\. However, the following Regions do not support license management across AWS accounts:
+ China \(Beijing\)
+ China \(Ningxia\)

**Topics**
+ [License configurations](license-configurations.md)
+ [License rules](license-rules.md)
+ [License reports](license-reporting.md)
+ [License type conversions](license-conversion.md)
+ [Host resource groups](host-resource-groups.md)
+ [Resource inventory](inventory.md)
+ [Granted licenses](granted-licenses.md)
+ [Seller issued licenses](seller-issued-licenses.md)
+ [Delegated administration](delegated-administrator.md)
+ [Settings](settings.md)
+ [Dashboard](dashboard.md)