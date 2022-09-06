# Prerequisites<a name="conversion-prerequisites"></a>

To convert license types with License Manager, verify that the following prerequisites are met:
+ Your AWS account must be onboarded to License Manager\. See [Getting started with AWS License Manager](getting-started.md)\.
+ Instances that were originally launched from an Amazon provided Amazon Machine Image \(AMI\) are not eligible for license type conversion to BYOL\. The original Amazon EC2 instance must be launched from your own virtual machine \(VM\) image\. For more information about converting a VM to Amazon EC2, see [VM Import/Export](https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-image-import.html#import-vm-image)\. 
+ You must provide the media for installing SQL Server on instances that are launched from your own VM image\.
+ The target instance must be in a stopped state before you convert the license type\. When a license license type conversion is in progress, you can start and stop the target instance\.
+ The target instance must be configured with AWS Systems Manager Inventory and your IAM user or role must have the following permissions:
  + `ssm:GetInventory`
  + `ssm:StartAutomationExecution`
  + `ssm:GetAutomationExecution`
  + `ssm:SendCommand`
  + `ssm:GetCommandInvocation`
  + `ssm:DescribeInstanceInformation`
  + `ec2:DescribeInstances`
  + `ec2:StartInstances`
  + `ec2:StopInstances`
  + `license-manager:CreateLicenseConversionTaskForResource`
  + `license-manager:GetLicenseConversionTask`
  + `license-manager:ListLicenseConversionTasks`
  + `license-manager:GetLicenseConfiguration`
  + `license-manager:ListUsageForLicenseConfiguration`
  + `license-manager:ListLicenseSpecificationsForResource`
  + `license-manager:ListAssociationsForLicenseConfiguration`
  + `license-manager:ListLicenseConfigurations`

  For more information about Systems Manager Inventory, see [AWS Systems Manager Inventory](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html)\. 