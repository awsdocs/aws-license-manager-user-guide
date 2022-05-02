# Granted licenses in License Manager<a name="granted-licenses"></a>

Granted licenses are licenses for products that your organization purchased from AWS Marketplace, [AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/what-is.html), or directly from a seller who integrated their software with managed entitlements\. License administrators can use AWS License Manager to govern the use of these licenses and to distribute rights of use, known as entitlements, to specific AWS accounts\.

After a license administrator distributes an entitlement from an AWS Marketplace license to an AWS account, and the recipient accepts and activates the granted license, the subscription is available to the AWS account through AWS Marketplace\. The account also has access to the product\. For example, if a license administrator purchases an Amazon Machine Image \(AMI\) from AWS Marketplace and distributes an entitlement to your AWS account, you can launch Amazon EC2 instances from the AMI using AWS Marketplace and Amazon EC2\.

Data licenses distributed to AWS Data Exchange products are available to the AWS account through AWS Data Exchange\.

Before you can distribute licenses from AWS Marketplace, you must enable subscription sharing\. For more information, see [Sharing subscriptions in an organization](https://docs.aws.amazon.com/marketplace/latest/buyerguide/organizations-sharing.html)\.

## Manage your granted licenses<a name="manage-granted-licenses"></a>

After you purchase subscriptions from AWS Marketplace or AWS Data Exchange, purchase products from sellers that use License Manager to distribute licenses, or receive a grant from a license administrator, the granted licenses appear in the License Manager console\. Recipients must accept and activate granted licenses before they can use the product\.

How you accept and activate a license depends on whether the license is from AWS Marketplace, if your account is member account in an organization for AWS Organizations, and whether [all features](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) is enabled for your organization\.

Granted licenses require cross\-Region replication of license metadata\. License Manager automatically replicates each granted license and its associated information to other Regions\. This enables you to have a centralized view across all Regions where licenses are granted to you\.

**Licenses from AWS Marketplace and AWS Data Exchange**
+ Licenses for subscriptions that you purchase from AWS Marketplace are automatically accepted and activated\.
+ If the management account for an organization with all features enabled purchases a subscription from AWS Marketplace and distributes licenses to member accounts, the licenses are automatically accepted in the member accounts\. Either the management account or the member accounts can later activate the license\.
+ If the management account for an organization with only consolidated billing features enabled purchases a subscription from AWS Marketplace and distributes licenses to member accounts, each member account must accept and activate the license\.

**Licenses from a seller**
+ You must accept and activate licenses for products that you purchase from a seller that uses License Manager to distribute licenses\.
+ If the management account for an organization with all features enabled purchases a product from a seller and distributes licenses to member accounts, the licenses are automatically accepted in the member accounts\. Either the management account or the member accounts can later activate the license\.
+ If the management account for an organization with only consolidated billing features enabled purchases a product from a seller and distributes licenses to member accounts, each member account must accept and activate the license\.

**To manage your granted licenses**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Granted licenses**\.

1. \(Optional\) Use the filter options, such as the following, to scope the list of licenses that are displayed\.
   + Product name – The name of the product\.
   + Issuer – The entity that issued the license\. For example, licenses created by AWS Marketplace have an issuer of **AWS/Marketplace**\.
   + Seller of record – The entity that sold the product\.
   + Status – The status of the license\. For example, **Available**\.
   + Grant status – The status of the grant\. For example, **Pending acceptance**\.

1. To view additional information about the license, choose the license ID to open the license detail page\.

1. If the license issuer is an entity other than AWS Marketplace, the initial grant status is **Pending acceptance**\. Do one of the following:
   + Choose **Accept & activate license**\. The resulting grant status is **Active**\.
   + Choose **Accept license**\. The resulting grant status is **Disabled**\. When you are ready to use the license, choose **Activate license**\.
   + Choose **Reject license**\. The resulting grant status is **Rejected**\. After you reject a license, you cannot activate it\.

1. To stop using an active license, choose **Deactivate license**\. When you are ready to use it again, choose **Activate license**\.

**To manage your granted licenses using the command line**
+ [accept\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/accept-grant.html) \(AWS CLI\)
+ [create\-grant\-version](https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-grant-version.html) \(AWS CLI\)
+ [get\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/get-grant.html) \(AWS CLI\)
+ [list\-licenses](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-licenses.html) \(AWS CLI\)
+ [list\-received\-grants](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-grants.html) \(AWS CLI\)
+ [list\-received\-licenses](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-received-licenses.html) \(AWS CLI\)
+ [reject\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/reject-grant.html) \(AWS CLI\)

## Distribute an entitlement<a name="distribute-entitlement"></a>

If you are the license administrator, you can create a grant to distribute access to a license to another AWS account in your organization\. You can create up to 2,000 grants per license\.

**To create a grant**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the navigation pane, choose **Granted licenses**\.

1. Choose a license ID to open the license detail page\.

1. From the **Grants** section, choose **Create grant**\.

1. On the **Grant details** panel, do the following:

   1. Enter a name for the grant to help you identify the purpose or recipient of the grant\.

   1. Enter the AWS account ID of the grant recipient\.
**Note**  
You can also enter the AWS Organizations ID for your organization to grant the entitlement to all accounts in your organization at once\. For more information, see [Distribution to AWS Organizations](#distribute-to-organization)\.

   1. Choose **Create grant**\.

1. When you return to the license detail page, you'll see an entry for the grant in the **Grants** panel\. The initial status of the grant is **Pending acceptance**\. The status changes to **Active** when the recipient accepts the grant or **Rejected** when the recipient rejects the grant\.

**To create a grant using the command line**
+ [create\-grant](https://docs.aws.amazon.com/cli/latest/reference/license-manager/create-grant.html) \(AWS CLI\)
+ [list\-distributed\-grants](https://docs.aws.amazon.com/cli/latest/reference/license-manager/list-distributed-grants.html) \(AWS CLI\)

## Grant acceptance and activation<a name="grant-acceptance"></a>

A granted license must be accepted and activated in the grantee account before it can be used\.

By default, the grant details page for a granted license has a status of **Pending acceptance**\. You can choose to **Accept**, **Accept and Activate**, or **Reject** the license\.

**Note**  
You can't activate two licenses for the same product from AWS Marketplace at the same time\. If you have two subscriptions \(for example, the public offer for a product and a private offer, or a subscribed license for a product and a granted license for the same product\), you must deactivate the one that you are not using before you can activate the other\.

Grants that are accepted but not yet activated have a status of **Disabled**\. Accepted and activated grants have a status of **Active**\.

**Note**  
It is possible to have grants from the management account of your organization automatically accepted\. To enable grant auto\-acceptance, link your organization accounts via the AWS License Manager console [settings](https://docs.aws.amazon.com/license-manager/latest/userguide/settings.html) from the management account\.

## Distribution to AWS Organizations<a name="distribute-to-organization"></a>

If you are a license administrator operating in the management account of an organization with [ all features](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) enabled, you can distribute your licenses to all accounts in your organization at one time\. To distribute your license to all accounts with one grant, choose your organization ID rather than a single account ID when [ distributing your entitlement](https://docs.aws.amazon.com/license-manager/latest/userguide/granted-licenses.html#distribute-entitlement)\. In the console, you can specify the organization ID or the organization ARN\. Here is an example organization ARN: `arn:aws:organizations::<account-id-of-management-account>:organization/<organization-id>`\. You must use the ARN when using the [AWS License Manager API](https://docs.aws.amazon.com/license-manager/latest/APIReference/)\.

**Note**  
In order to grant a license to your AWS Organizations ID, you must first link AWS Organizations accounts via the AWS License Manager console settings\. For more information, see [Settings in License Manager](settings.md)\.

The grant details page displays the list of accounts that you have granted access to the entitlement\. After distributing a license to your organization, you can deactivate or activate the licenses individually on each account\.

## License status<a name="grant-statuses"></a>

Licenses have two statuses: The **License status**, which shows the overall availability and sharability of the license, and the **Grant status**, which shows the ability to use the license\.


**License statuses**  

| Status | Description | 
| --- | --- | 
|   Available  |   The license is available to use and share\.  | 
|   Deleted  |   The license is not available to use because the license agreement has been canceled\.  | 
| Deactivated | The license it not available to use because it has been deactivated by the license issuer\. | 
| Expired | The license is not available to use because it has reached the end of term\. | 


**Grant statuses**  

| Status | Description | 
| --- | --- | 
|   Pending acceptance  |   The grant has been created and the grant recipient has not yet accepted it\.  | 
|   Disabled  |   The grant has been accepted by the recipient but has not been activated for use\.  | 
|   Active  |   The grant has been accepted and activated for use\. The licensed resource can be used\.  | 
|   Rejected  |   The grant recipient has rejected the grant\.  | 
|   Deleted  |   The grantor has deleted the grant\.  | 
|   Workflow complete  |   The grant is a grant to an organization, and the workflow to distribute or recall the grant has been completed\. The grant details show the status of sub\-grants to each account in the organization\.  | 

## Metrics for buyer accounts<a name="how-metrics-emit-buyers"></a>

When you record usage against a seller issued license for a buyer account, License Manager emits a CloudWatch metric to the seller account, root buyer account, and the account against which the usage is being recorded\.

In addition, when a seller or independent software vendor \(ISV\) application records usage against a license for a buyer account, the account in which usage is being recorded and the root buyer account see a CloudWatch widget with usage records in their License Manager console\. Buyers can also see metrics for accounts that they have distributed licenses to in AWS Organizations\. These graphs are available for every license for which usage records have been sent\.

### Usage dashboard example<a name="usage-dashboard-example"></a>

![\[This is an example image of the Usage Dashboard.\]](http://docs.aws.amazon.com/license-manager/latest/userguide/images/license-manager-usage-api-usage-dash.png)