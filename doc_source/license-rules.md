# License rules in License Manager<a name="license-rules"></a>

After license configuration rules are in place, they can be attached to the relevant launch mechanisms, where they can directly prevent the deployment of new resources that are non\-compliant\. Users in your organization can seamlessly launch EC2 instances from designated AMIs, and administrators can track license inventory through the built\-in License Manager dashboard\. Launch controls and dashboard alerts allow easier compliance enforcement\. 

**Important**  
AWS does not participate in the audit process with software vendors\. Customers are responsible for compliance and assume the responsibility of carefully understanding and capturing rules into License Manager based on their licensing agreements\. 

License tracking works from the time rules are attached to an instance until its termination\. You define your usage limits and licensing rules, and License Manager tracks deployments while also alerting you to rule violations\. If you have configured hard limits, License Manager can prevent resources from launching\. 

When a tracked server is stopped or terminated, its license is released and returned to the pool of available licenses\.

Because organizations have differing approaches to operations and compliance, License Manager supports multiple launch mechanisms:
+ **Manual association of license configurations with AMIs** — For tracking licenses for operating system or other software, you can attach licensing rules to AMIs before publishing them for broader use in your organization\. Any deployments from these AMIs are then automatically tracked with License Manager without requiring any additional actions by users\. You can also attach licensing rules to your current AMI building mechanisms such as [Systems Manager Automation](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-automation.html), [VM Import/Export](https://docs.aws.amazon.com/vm-import/latest/userguide/), and [Packer](https://www.packer.io/docs/builders/amazon.html)\.
+ **Amazon EC2 launch templates and AWS CloudFormation** — If attaching licensing rules to AMIs is not a preferred option, you can specify them as optional parameters in [EC2 launch templates](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html) or [AWS CloudFormation templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/)\. Deployments using these templates are tracked using License Manager\. You can enforce rules on EC2 launch templates or AWS CloudFormation templates by specifying one or more license configuration IDs in the **License Configurations** field\.

AWS treats license\-tracking data as sensitive customer data accessible only through the AWS account that owns it\. AWS does not have access to your license\-tracking data\. You control your license\-tracking data and you can delete it at any time\.

## Associating license configurations and AMIs<a name="ami-associations"></a>

The following procedure demonstrates how to associate license configurations with AMIs using the License Manager console\. The procedure assumes that you have at least one existing license configuration\. You can associate license configurations with any AMI that you have access to, whether owned or shared\. If an AMI was shared with you, you can associate it with the license configuration in the current account\. Otherwise, you can specify whether the AMI is associated with the license configuration across all accounts or only in the current account\.

If you associate an AMI with a license configuration across all accounts, you can track instance launches from the AMI across accounts\. When a hard limit is reached, License Manager blocks additional instance launches\. When a soft limit is reached, License Manager notifies you of additional instance launches\. You must ensure that users can't get access to the AMI through another mechanism, such as copying the AMI or creating an AMI from an instance launched from the AMI\.

**To associate a license configuration and an AMI**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **License configurations**\.

1. Choose the name of the license configuration to open the license details page\. To view the currently associated AMIs, choose **Associated AMIs**\.

1. Choose **Associate AMI**\.

1. For **Available AMIs**, select one or more AMIs and choose **Associate**\.
   + If your account owns at least one of the AMIs, you are prompted to choose an AMI association scope for the AMIs that you own\. Any AMIs that were shared with from another account are associated with only your account\. Choose **Confirm**\.
   + If the AMIs were shared with you from another account, they are associated with only your account\.

   The newly associated AMIs now appear on the **Associated AMIs** tab on the license details page\.

## Disassociating license configurations and AMIs<a name="ami-disassociation"></a>

The following procedure demonstrates how to disassociate license configurations from AMIs using the License Manager console\. You cannot disassociate a deregistered AMI\. License Manager checks for deregistered AMIs every 8 hours and automatically disassociates them\.

**To disassociate a license configuration and an AMI**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **License configurations**\.

1. Choose the name of the license configuration to open the license details page\.

1. Choose **Associated AMIs**\.

1. Select the AMI and choose **Disassociate AMI**\.