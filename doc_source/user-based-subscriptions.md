# User\-based subscriptions in AWS License Manager<a name="user-based-subscriptions"></a>

AWS License Manager user\-based subscriptions provide the ability to purchase fully compliant Amazon provided licenses for Microsoft Visual Studio with a per user subscription fee\. The licensed software is available to users when you create user\-based subscriptions and associate them with Amazon Elastic Compute Cloud \(EC2\) instances providing the product\. Amazon EC2 provides pre\-configured Amazon Machine Images \(AMIs\) with the supported software, along with license included Windows Server licenses, to use without long\-term licensing commitments\.

You must associate users with [AWS Directory Service for Microsoft Active Directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_microsoft_ad.html) to use the supported software within the EC2 instances\. Multiple associated users can utilize the same EC2 instances by using Remote Desktop software\. [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html) is used to configure and harden the provisioned license included instances\.

Each [vCPU](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html) for the EC2 license included Windows Server instance, as well as each associated user, incurs charges\. User\-based subscriptions are billed from the first of the month to the end of the month\. Utilizing Amazon EC2 Reserved Instances and Savings Plan pricing models can assist with optimizing costs while running the instances providing user\-based subscription products\. For more information, see [Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-reserved-instances.html) in the *Amazon Elastic Compute Cloud User Guide*\.

**Contents**
+ [Supported software for user\-based subscriptions](user-based-subscriptions-supported-software.md)
+ [Considerations](user-based-subscriptions-considerations.md)
+ [Prerequisites](user-based-subscriptions-prerequisites.md)
+ [Getting started with user\-based subscriptions](user-based-subscriptions-getting-started.md)
  + [Step 1: Configure AWS Directory Service for Microsoft Active Directory](user-based-subscriptions-getting-started.md#user-based-subscriptions-configure-ad)
  + [Step 2: Subscribe to a product](user-based-subscriptions-getting-started.md#user-based-subscriptions-subscribe-products)
  + [Step 3: Launch an instance to provide user\-based subscriptions](user-based-subscriptions-getting-started.md#user-based-subscriptions-launch-instance)
  + [Step 4: Associate users to an instance](user-based-subscriptions-getting-started.md#user-based-subscriptions-associate-users)
  + [Step 5: Connect to a user\-based subscription instance](user-based-subscriptions-getting-started.md#user-based-subscriptions-connect)
+ [Modifying directory settings for user\-based subscriptions](user-based-subscriptions-modify-ad.md)
+ [Disassociating users from user\-based subscriptions](user-based-subscriptions-disassociate-users.md)
+ [Unsubscribing users from user\-based subscriptions](user-based-subscriptions-unsubscribe-users.md)
+ [Terminating EC2 instances providing user\-based subscriptions](user-based-subscriptions-terminate-instances.md)
+ [Removing a directory for user\-based subscriptions](user-based-subscriptions-remove-ad.md)
+ [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md)
  + [Troubleshooting instance compliance](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-compliance)
  + [Troubleshooting instance connectivity](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-instance-connectivity)
  + [Troubleshooting domain join](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-domain-join)
  + [Troubleshooting Systems Manager connectivity](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-systems-manager-connectivity)
  + [Troubleshooting Systems Manager Run Command](user-based-subscriptions-troubleshoot.md#user-based-subscriptions-troubleshoot-systems-manager-commands)