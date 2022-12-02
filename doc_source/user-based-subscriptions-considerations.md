# Considerations<a name="user-based-subscriptions-considerations"></a>

The following considerations apply when utilizing user\-based subscriptions with License Manager:
+ **Win Remote Desktop Services SAL** licenses cannot be used separately from the supported user\-based subscription products\.
+ To stop incurring charges for user\-based subscriptions, you must disassociate the user from all instances they are associated with\. For more information, see [Disassociating users from user\-based subscriptions](user-based-subscriptions-disassociate-users.md)\.
+ When you configure your directory with Microsoft Office products, your VPC must have [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html) provisioned in at least one subnet\. If you want to remove all VPC endpoint resources created by License Manager, you must perform the following actions:
  + Disassociate all users from their user\-based subscriptions\. For more information, see [Disassociating users from user\-based subscriptions](user-based-subscriptions-disassociate-users.md)\.
  + Remove any directory that is configured from the License Manager settings\. For more information, see [Removing a directory for user\-based subscriptions](user-based-subscriptions-remove-ad.md)\.
  + Terminate all instances providing user\-based subscription products\. For more information, see [Terminating EC2 instances providing user\-based subscriptions](user-based-subscriptions-terminate-instances.md)\.
+ The tag key of `AWSLicenseManager` with the value of `UserSubscriptions` assigned by License Manager to your instances must not be altered or deleted\.
+ The two Elastic Network Interfaces \(ENIs\) created for License Manager must not be altered or deleted for the service to function\.
+ The objects that License Manager creates in the AWS Managed Microsoft AD directory's **AWS Reserved** organizational unit \(OU\) must not be altered or deleted\.
+ The instances deployed for user\-based subscriptions must be managed nodes with AWS Systems Manager and joined to the same domain\. For information on keeping your instances managed by Systems Manager, see the [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-systems-manager-connectivity) section of this guide\.
+ The user\-based subscriptions feature is not available in the Asia Pacific \(Jakarta\) Region\.