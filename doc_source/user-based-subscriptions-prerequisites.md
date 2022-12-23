# Prerequisites<a name="user-based-subscriptions-prerequisites"></a>

The following prerequisites must be implemented in your environment before you can create user\-based subscriptions\.
+ You must allow License Manager to create a service\-linked role in order to onboard your AWS account for user\-based subscriptions\. A prompt will appear once in the **User\-based subscriptions** section of the License Manager console in which you can agree to give License Manager permission to create the required service\-linked role\. After you grant permission to License Manager, you can choose **Create**, to create the service\-linked role\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.
+ You must have an AWS Managed Microsoft AD to associate users with\. For more information on creating an AWS Managed Microsoft AD, see [AWS Managed Microsoft AD prerequisites](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_getting_started_prereqs.html) and [Create your AWS Managed Microsoft AD directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_getting_started_create_directory.html) in the *AWS Directory Service User Guide*\.
+ Users must be provisioned in AWS Managed Microsoft AD to utilize the user\-based subscriptions\. For more information, see [Manage users and groups in AWS Managed Microsoft AD](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_manage_users_groups.html) in the *AWS Directory Service Administration Guide*\.
+ Outbound internet access from the instances providing user\-based subscriptions, or [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html), must be configured for your instances to communicate with AWS Systems Manager\. For more information, see [Setting up Systems Manager for EC2 instances](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-setting-up-ec2.html) in the *AWS Systems Manager User Guide*\.
+ You must configure DNS forwarding for any additional VPCs to the AWS Managed Microsoft AD you register for user\-based subscriptions\. You can use Amazon Route 53 or another DNS service for DNS forwarding\. For more information, see the blog post [Integrating your Directory Service’s DNS resolution with Amazon Route 53 Resolvers](http://aws.amazon.com/blogs/networking-and-content-delivery/integrating-your-directory-services-dns-resolution-with-amazon-route-53-resolvers/)\.
+ If you subscribe to Microsoft Office with user\-based subscriptions, you must:
  + Enable **DNS hostnames** and **DNS resolution** for your VPC\. For more information, see [View and update DNS attributes for your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html#vpc-dns-updating)\.
  + Ensure that the instances launched to provide user\-based subscriptions with Microsoft Office have a route to the subnet where the VPC endpoints are provisioned\.
  + Identify or create a security group for your VPC endpoints that permits inbound TCP port 1688 connectivity\. This security group will be specified when you configure your virtual private cloud settings\. For more information, see [Work with security groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#working-with-security-groups)\. License Manager will associate this security group to the VPC endpoints it creates on your behalf while configuring the VPC\. For more information about VPC endpoints, see [Access an AWS service using an interface VPC endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html)\.
  + Identify or create a security group for the instances launched to provide used\-based subscriptions that permits inbound TCP port 3389 connectivity from your approved connection sources\. The security group should also permit outbound TCP port 1688 connectivity to reach the VPC endpoints\. For more information, see [Work with security groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#working-with-security-groups)\.

    If you are getting ready to use user\-based subscriptions for the first time, complete the prerequisites listed and see [Getting started with user\-based subscriptions](user-based-subscriptions-getting-started.md)\. If you are already set up for user\-based subscriptions, and would like to add these products to your AWS Managed Microsoft AD and configure your VPC for Microsoft Office products, complete the prerequisites listed, and see [Modifying directory settings for user\-based subscriptions](user-based-subscriptions-modify-ad.md)\.
+ You must have an instance profile role attached to instances providing the user\-based subscription products that allows for the resource to be managed by AWS Systems Manager\. For more information, see [Create an IAM instance profile for Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-instance-profile.html) in the *AWS Systems Manager User Guide*\.
**Warning**  
Instances that provide user\-based subscriptions must be managed by AWS Systems Manager in order to have a healthy status\. Additionally, your instances must be able to activate their user\-based subscription licensing and remain in compliance after license activation\. License Manager will attempt to recover unhealthy instances, but instances that are not able to be return to a healthy status will be terminated\. For troubleshooting information on keeping your instances managed by Systems Manager, and instance compliance, see the [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md) section of this guide\.
+ To create user\-based subscriptions, your IAM user or role must have the following permissions:
  + `ec2:CreateNetworkInterface`
  + `ec2:DeleteNetworkInterface`
  + `ec2:DescribeNetworkInterfaces`
  + `ec2:CreateNetworkInterfacePermission`
  + `ec2:DescribeSubnets`
  + `ds:DescribeDirectories`
  + `ds:AuthorizeApplication`
  + `ds:UnauthorizeApplication`
  + `ds:GetAuthorizedApplicationDetails`
  + `ds:DescribeDomainControllers`
+ To create user\-based subscriptions for Microsoft Office products, your IAM user or role must also have these additional permissions:
  + `ec2:CreateVpcEndpoint`
  + `ec2:DeleteVpcEndpoints`
  + `ec2:DescribeVpcEndpoints`
  + `ec2:ModifyVpcEndpoint`
  + `ec2:DescribeSecurityGroups`