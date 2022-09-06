# Prerequisites<a name="user-based-subscriptions-prerequisites"></a>

The following prerequisites must be implemented in your environment before you can create user\-based subscriptions\.
+ You must allow License Manager to create a service\-linked role in order to onboard your AWS account for user\-based subscriptions\. A prompt will appear once in the **User\-based subscriptions**section of the License Manager console in which you can agree to give License Manager permission to create the required service\-linked role\. After you grant permission to License Manager, you can choose **Create**, to create the service\-linked role\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.
+ You must have an AWS Managed Microsoft AD to associate users with\. For more information on creating an AWS Managed Microsoft AD, see the [AWS Managed Microsoft AD prerequisites](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_getting_started_prereqs.html) page and the [Create your AWS Managed Microsoft AD directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_getting_started_create_directory.html) page in the *AWS Directory Service User Guide*\.
+ Users must be provisioned in AWS Managed Microsoft AD to utilize the user\-based subscriptions\. For more information, see [Manage users and groups in AWS Managed Microsoft AD](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_manage_users_groups.html) in the *AWS Directory Service Administration Guide*\.
+ Outbound internet access from the instances providing user\-based subscriptions or VPC endpoints, must be configured for your instances to communicate with AWS Systems Manager\. For more information, see [Setting up Systems Manager for EC2 instances](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-setting-up-ec2.html) in the *AWS Systems Manager User Guide*\.
+ You must have an instance profile role for instances providing the user\-based subscription products that allows for connectivity to AWS Systems Manager\. For more information, see [Create an IAM instance profile for Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-instance-profile.html) in the *AWS Systems Manager User Guide*\.
**Warning**  
Instances that provide user\-based subscriptions must be managed by AWS Systems Manager in order to have a healthy status\. License Manager will attempt to recover unhealthy instances, but instances that are not able to be return to a healthy status will be terminated\. For troubleshooting information on keeping your instances managed by Systems Manager, and instance compliance, see the [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md) section of this guide\.
+ To create user\-based subscriptions, your IAM user or role must have the following permissions:
  + ec2:CreateNetworkInterface
  + ec2:DeleteNetworkInterface
  + ec2:DescribeNetworkInterfaces
  + ec2:CreateNetworkInterfacePermission
  + ec2:DescribeSubnets
  + ds:DescribeDirectories
  + ds:AuthorizeApplication
  + ds:UnauthorizeApplication
  + ds:GetAuthorizedApplicationDetails
  + ds:DescribeDomainControllers