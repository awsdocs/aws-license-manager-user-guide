# Considerations<a name="user-based-subscriptions-considerations"></a>

The following considerations apply when utilizing user\-based subscriptions with License Manager:
+ To stop incurring charges for user\-based subscriptions, you must disassociate the user from all instances they are associated with\.
+ The tag key of `AWSLicenseManager` with the value of `UserSubscriptions` assigned by License Manager to your instances must not be altered or deleted\.
+ The two Elastic Network Interfaces \(ENIs\) created for License Manager must not be altered or deleted for the service to function\.
+ Objects in the reserved Organizational Unit \(OU\) License Manager will create in the AWS Managed Microsoft AD directory must not be or altered deleted\.
+ The instances deployed for user\-based subscriptions must be managed nodes with Systems Manager and joined to the same domain\. For information on keeping your instances managed by AWS Systems Manager, see the [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-systems-manager-connectivity) section of this guide\.
+ The User\-based subscriptions feature is not available in the Asia Pacific \(Jakarta\) Region\.