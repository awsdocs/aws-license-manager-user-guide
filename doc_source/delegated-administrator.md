# Register a delegated administrator<a name="delegated-administrator"></a>

 You can delegate a member account from your organization to perform administrative tasks, such as sharing license configurations with other member accounts, performing cross\-account resource discovery, and distributing managed entitlements to other member accounts\. Only member accounts that are part of your AWS Organizations can be registered as a delegated administrator\. For more information about joining an organization, see [Inviting an AWS account to join your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts_invites.html)\.

Your can register one delegated administrator per organization\. Before you register a delegated administrator, you must enable trusted access with AWS Organizations\. For more information, see [Enable trusted access with AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-license-manager.html)\. 

**Important**  
Once registered, the delegated administrator has visibility into EC2 instances owned by accounts in your organization\.

The following AWS Regions support License Manager delegated administrators:
+ US East \(Ohio\)
+ US East \(N\. Virginia\)
+ US West \(N\. California\)
+ US West \(Oregon\)
+ Asia Pacific \(Mumbai\)
+ Asia Pacific \(Seoul\)
+ Asia Pacific \(Singapore\)
+ Asia Pacific \(Sydney\)
+ Asia Pacific \(Tokyo\)
+ Asia Pacific \(Hong Kong\)
+ Middle East \(Bahrain\)
+ Canada \(Central\)
+ Europe \(Frankfurt\)
+ Europe \(Ireland\)
+ Europe \(London\)
+ Europe \(Paris\)
+ Europe \(Stockholm\)
+ Europe \(Milan\)
+ Africa \(Cape Town\)
+ South America \(São Paulo\)
+ AWS GovCloud \(US\-East\)
+ AWS GovCloud \(US\-West\)

You can register and deregister delegated administrators using the [AWS License Manager console](https://console.aws.amazon.com/license-manager), [AWS CLI](http://aws.amazon.com/cli), or [AWS SDKs\.](http://aws.amazon.com/tools) 

**Topics**
+ [Register \(console\)](#register-delegated-admin-console)
+ [Deregister \(console\)](#deregister-delegated-admin-console)
+ [Register \(AWS CLI\)](#register-delegated-admin-cli)
+ [Deregister \(AWS CLI\)](#deregister-delegated-admin-cli)

## Register a delegated administrator \(console\)<a name="register-delegated-admin-console"></a>

To register a delegated administrator using the AWS License Manager console, perform the following steps:

1. Sign in to AWS as the administrator of the management account\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Settings** from the left navigation pane\.

1. Under **Delegated administrators**, choose **Delegate administrator**\.

1. To register a delegated administrator, enter the account ID and select **Delegate**\.

1. A message indicates that the specified account has been successfully registered as a delegated administrator\.

## Deregister a delegated administrator \(console\)<a name="deregister-delegated-admin-console"></a>

To deregister a delegated administrator using the AWS License Manager console, perform the following steps:

1. Sign in to AWS as the administrator of the management account\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Settings** from the left navigation pane\.

1. Under **Delegated adminstrators**, choose **Remove**\.

1. Verify successful deregistering of delegated administrator by choosing **Remove** again\.

## Register a delegated administrator \(AWS CLI\)<a name="register-delegated-admin-cli"></a>

To register a delegated administrator using the AWS CLI, perform the following steps:

1. From the command line, run the following AWS CLI command:

   ```
   aws organizations register-delegated-administrator --service-principal=license-manager.amazonaws.com --account-id=<account-id>
   ```

1. Run the following command to verify that the specified account is successfully registered as the delegated administrator:

   ```
   aws organizations list-delegated-administrators  --service-principal=license-manager.amazonaws.com
   ```

## Deregister a delegated administrator \(AWS CLI\)<a name="deregister-delegated-admin-cli"></a>

To deregister a delegated administrator using the AWS CLI, perform the following steps:

1. From the command line, run the following AWS CLI command:

   ```
   aws organizations deregister-delegated-administrator --service-principal=license-manager.amazonaws.com --account-id=<account-id>
   ```

1. Run the following command to verify that the specified account is successfully deregistered as the delegated administrator:

   ```
   aws organizations list-delegated-administrators  --service-principal=license-manager.amazonaws.com
   ```

You can register a deregistered account again at any time\.