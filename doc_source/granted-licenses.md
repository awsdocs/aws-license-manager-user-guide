# Granted licenses in License Manager<a name="granted-licenses"></a>

Granted licenses are licenses for products that your organization purchased from [AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/what-is-marketplace.html), [AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/what-is.html), or directly from a seller who integrated their software with managed entitlements\. License administrators can use AWS License Manager to govern the use of these licenses and to distribute rights of use, known as entitlements, to specific AWS accounts\.

Data licenses distributed to AWS Data Exchange products are available to the AWS account through AWS Data Exchange\. Before you can distribute licenses from AWS Marketplace, you must enable subscription sharing\. For more information, see [Sharing subscriptions in an organization](https://docs.aws.amazon.com/marketplace/latest/buyerguide/organizations-sharing.html)\.

After a license administrator distributes an entitlement from an AWS Marketplace license to an AWS account, and the recipient accepts and activates the granted license, the subscription is available to the AWS account through AWS Marketplace\. The account also has access to the product\. For example, if a license administrator purchases an Amazon Machine Image \(AMI\) from AWS Marketplace and distributes an entitlement to your AWS account, you can launch Amazon EC2 instances from the AMI using AWS Marketplace and Amazon EC2\.

## View your granted licenses<a name="granted-licenses-views"></a>

License Manager displays tabs to view and manage your granted licenses based on the permissions you are authenticated with\. The granted license page can display the following tabs: 

**My licenses**  
This tab is available for any user that has access to view the granted licenses in License Manager\. The tab has a **My granted licenses** section which includes information about each license such as the **License ID** and **Product name**\. From this page you can view additional information about each license\.

**License summary \(for organization administrators\)**  
This tab is available only for organization administrators\. The tab has a **Totals** section which lists the total amount of products and granted licenses across all accounts in your organization\. It also shows a **Products** section which includes a table detailing the properties of each product, such as the **Product name** and **Number of granted licenses**\.

**Aggregated licenses \(for organization administrators\)**  
This tab is available only for organization administrators\. This tab has a section detailing **Granted licenses for my organization** which includes information about each license such as the **License ID** and **Product name**\. From this page you can view additional information about each license\.

## Manage your granted licenses<a name="manage-granted-licenses"></a>

Licenses that have been granted to you will appear in the License Manager console\. Recipients must accept and activate granted licenses before they can use the product\. How you accept and activate a license depends on whether the license is from AWS Marketplace, if your account is member account in an organization for AWS Organizations, and whether all features is enabled for your organization\.

Granted licenses require cross\-Region replication of license metadata\. License Manager automatically replicates each granted license and its associated information to other AWS Regions\. This enables you to have a centralized view across all Regions where licenses are granted to you\.

**Licenses from AWS Marketplace and AWS Data Exchange**
+ Licenses for subscriptions that you purchase are automatically accepted and activated\.
+ If the management account for an organization with all features enabled purchases a subscription and distributes licenses to member accounts, the licenses are automatically accepted in the member accounts\. Either the management account or the member accounts can later activate the license\.
+ If the management account for an organization with only consolidated billing features enabled purchases a subscription and distributes licenses to member accounts, each member account must accept and activate the license\.

**Licenses from a seller**
+ You must accept and activate licenses for products that use License Manager to distribute licenses\.
+ If the management account for an organization with all features enabled purchases a product and distributes licenses to member accounts, the licenses are automatically accepted in the member accounts\. Either the management account or the member accounts can later activate the license\.
+ If the management account for an organization with only consolidated billing features enabled purchases a product and distributes licenses to member accounts, each member account must accept and activate the license\.

------
#### [ Console \(My licenses\) ]

You can view and manage granted licenses for a single AWS account\.

**To manage granted licenses in your account**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Granted licenses**\.

1. Choose the **My licenses** tab if it is not the current selection\.

1. \(Optional\) Use the filter options, such as the following, to scope the list of licenses that are displayed\.
   + Product SKU – The product identifier for this license, as defined by the license issuer when creating the license\. The same product SKU might exist across multiple ISVs\.
   + Recipient – The ARN of the license recipient\.
   + Status – The status of the license\. For example, **Available**\.

1. To view additional information about the license, choose the license ID to open the license detail page\.

1. If the license issuer is an entity other than AWS Marketplace, the initial grant status is **Pending acceptance**\. Do one of the following:
   + Choose **Accept & activate license**\. The resulting grant status is **Active**\.
   + Choose **Accept license**\. The resulting grant status is **Disabled**\. When you are ready to use the license, choose **Activate license**\.
   + Choose **Reject license**\. The resulting grant status is **Rejected**\. After you reject a license, you cannot activate it\.

If you don't want to continue using a license that was activated, you can return to the license details page and choose **Deactivate license**\. If you want to continue using a license that was deactivated, return to the license details page and choose **Activate license**\.

------
#### [ Console \(Aggregated licenses\) ]

You can view your granted licenses that have been aggregated from all accounts in your organization\.

**Important**  
In order to use the organization wide view for your granted licenses, you must first link AWS Organizations using the AWS License Manager console settings\. For more information, see [Settings in License Manager](settings.md)\.

**To manage granted licenses across your accounts in AWS Organizations**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Granted licenses**\.

1. Choose the **Aggregated licenses** tab if it is not the current selection\.

1. \(Optional\) Use the filter options, such as the following, to scope the list of licenses that are displayed\.
   + Product SKU – The product identifier for this license, as defined by the license issuer when creating the license\. The same product SKU might exist across multiple ISVs\.
   + Beneficiary – The account in your organization that the license is granted to\.

1. To view additional information about the license, choose the license ID to open the license detail page\.

1. If the license issuer is an entity other than AWS Marketplace, do one of the following:
   + Choose **Activate license**\. The resulting grant status is **Active**\.
   + Choose **Deactivate license**\. The resulting grant status is **Deactivated**\.

If you don't want to continue using a license that was activated, you can return to the license details page and choose **Deactivate license**\. If you want to continue using a license that was deactivated, return to the license details page and choose **Activate license**\.

------
#### [ AWS CLI ]

You can use the AWS CLI to work with your granted licenses\.

**To manage your granted licenses using the command line**
+ [accept\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/accept-grant.html) \(AWS CLI\)
+ [create\-grant\-version](https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-grant-version.html) \(AWS CLI\)
+ [get\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/get-grant.html) \(AWS CLI\)
+ [list\-licenses](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-licenses.html) \(AWS CLI\)
+ [list\-received\-grants](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-grants.html) \(AWS CLI\)
+ [list\-received\-grants\-for\-organization](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-grants-for-organization.html) \(AWS CLI\)
+ [list\-received\-licenses](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-licenses.html) \(AWS CLI\)
+ [list\-received\-licenses\-for\-organization](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-licenses-for-organization.html) \(AWS CLI\)
+ [reject\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/reject-grant.html) \(AWS CLI\)

------

## Distribute an entitlement<a name="distribute-entitlement"></a>

If you are a license administrator operating in the management account of your organization with [all features](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) enabled, you can distribute entitlements to your organization from your granted licenses by creating a grant\.

You can specify the recipient of the grant as one of the following:
+ An AWS account, which includes only the account specified\.
+ An organizational unit \(OU\), which includes all accounts in the OU\.
+ An organization, which will include all accounts across your organization\.

**Note**  
You can create up to 2,000 grants per license\.

You can use either the AWS License Manager console or the AWS CLI to distribute your entitlements\. You can specify the organization ID or the organization ARN when creating a grant in the console, but the ARN format must be used with the AWS CLI\. For example, the ARNs will resemble the following:

**Organization ID ARN**  
`arn:aws:organizations::<account-id-of-management-account>:organization/o-<organization-id>`

**Organization OU ARN**  
`arn:aws:organizations::<account-id-of-management-account>:ou/o-<organization-id>/ou-<organizational-unit-id>`

------
#### [ Console ]

**To create a grant \(Console\)**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Granted licenses**\.

1. Choose a license ID to open the license detail page\.

1. From the **Grants** section, choose **Create grant**\.

1. On the **Grant details** panel, do the following:

   1. Enter a name for the grant to help you identify the purpose or recipient of the grant\.

   1. Enter the AWS account ID, AWS Organizations OU ID or ARN, or AWS Organizations ID or ARN of the grant recipient\.

   1. Choose **Create grant**\.

1. When you return to the license detail page, you'll see an entry for the grant in the **Grants** panel\. The initial status of the grant is **Pending acceptance**\. The status changes to **Active** when the recipient accepts the grant or **Rejected** when the recipient rejects the grant\.

------
#### [ AWS CLI ]

You can use the AWS CLI to distribute an entitlement\. You must use specify an organization ID or OU in ARN format when using the AWS License Manager API\.

**To create and list your grants using the AWS CLI:**
+ [https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-grant.html](https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-grant.html) \(AWS CLI\)
+ [https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-distributed-grants.html](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-distributed-grants.html) \(AWS CLI\)

------

The grant details page displays the list of accounts that you have granted access to the entitlement\. After distributing a license to your organization, you can deactivate or activate the licenses individually on each account\.

## Grant acceptance and activation<a name="grant-acceptance"></a>

A granted license must be accepted and activated before it can be used by the grant recipient\. By default, the grant details page for a granted license has a status of **Pending acceptance**\. You can choose to **Accept**, **Accept and Activate**, or **Reject** the license\. Grants that are accepted but not yet activated have a status of **Disabled**\. Accepted and activated grants have a status of **Active**\.

You can automatically accept grants that come from the management account of your organization\. To enable grant auto\-acceptance, link your organization accounts on the [settings](https://docs.aws.amazon.com/license-manager/latest/userguide/settings.html) page in the AWS License Manager console from the management account\.

You can't activate two licenses for the same product from AWS Marketplace at the same time\. If you have two subscriptions \(for example, the public offer for a product and a private offer, or a subscribed license for a product and a granted license for the same product\), you must deactivate the one that you are not using before you can activate the other\.

## License status<a name="grant-statuses"></a>

Licenses have two statuses: The **License status**, which shows the overall availability and sharability of the license, and the **Grant status**, which shows the ability to use the license\.

The follow table shows the various statuses for a granted license:


| Status | Description | 
| --- | --- | 
|  Available  |  The license is available to use and share\.  | 
|  Deleted  |  The license is not available to use because the license agreement has been canceled\.  | 
| Deactivated | The license is not available to use because it has been deactivated by the license issuer\. | 
| Expired | The license is not available to use because it has reached the end of term\. | 

The following table shows the various statuses for a grant:


| Status | Description | 
| --- | --- | 
|  Pending acceptance  |  The grant has been created and the grant recipient has not yet accepted it\.  | 
|  Disabled  |  The grant has been accepted by the grant recipient, but has not been activated for use\.  | 
|  Active  |  The grant has been accepted and activated for use by the grant recipient\. The licensed resource can be used\.  | 
|  Rejected  |  The grant has been rejected by the grant recipient\.  | 
|  Deleted  | The grant has been deleted by the grantor\. | 
|  Workflow complete  |  The grant to an organization has been distributed or recalled\. The grant details show the status of sub\-grants to each account in the organization\.  | 

## Metrics for buyer accounts<a name="how-metrics-emit-buyers"></a>

When a grant for a seller issued license is configured with **allow submission of usage records** selected, License Manager emits a CloudWatch metric to the seller account, root buyer account, and the account against which the usage is being recorded\. Buyer accounts are the AWS accounts who have purchased or been granted a seller issued license\. For more information, see [Granting licenses to customers](https://docs.aws.amazon.com/license-manager/seller-issued-licenses.html#isv-grant-licenses)\.

### Usage dashboard<a name="usage-dashboard-example"></a>

When a seller or independent software vendor \(ISV\) application records usage against a license for a buyer account, the account in which usage is being recorded and the root buyer account see a CloudWatch widget with usage records on the **Usage dashboard** page in the License Manager console\. Buyers can also see metrics for accounts that they have distributed licenses to in AWS Organizations\. The graphs on the **Usage dashboard** page are available for every license for which usage records have been sent\.

The following image is an example of the usage dashboard:

![\[This is an example image of the usage dashboard.\]](http://docs.aws.amazon.com/license-manager/latest/userguide/images/license-manager-usage-api-usage-dash.png)