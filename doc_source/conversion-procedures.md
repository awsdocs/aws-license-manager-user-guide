# Convert a license type<a name="conversion-procedures"></a>

You can convert license types using the License Manager console or the AWS CLI\. When you create a license type conversion task, License Manager validates the billing products on your instance\. If these preliminary validations are successful, License Manager creates a license type conversion task\. You can check the status of a license conversion task by using the `list-license-conversion-tasks` and ` get-license-conversion-task` AWS CLI commands\.

License Manager might update the resources associated with your customer managed licenses as part of a conversion task\. Specifically, for any customer managed license with automated discovery rules of type `License Included`, License Manager disassociates the resource in the license type conversion task from the license if the `license included` automated discovery rule explicitly excludes the resource\.

For example, if your customer managed license contains two automated discovery rules, and each rule excludes license included Windows Server, then a license type conversion from BYOL to license included Windows Server results in disassociation of the instance from the customer managed license\. However, if only one of the two automated discovery rules contains a `License Included` rule, then the instance is not disassociated\.

When the license type conversion task succeeds, its status changes from `IN_PROGRESS` to `SUCCEEDED`\. If License Manager encounters issues during the workflow, it updates the status of the license type conversion task to `FAILED`, and updates the status message with an error message\.

**Note**  
The billing product information on the AMI used to launch an instance does not change when you convert the license type\. To retrieve accurate billing information, use the Amazon EC2 [https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeInstances.html](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeInstances.html) API\. Additionally, if you have existing workflows that search for billing information from AMIs, update those workflows to use `DescribeInstances`\.

**Topics**
+ [License type conversion limits](#conversion-limits)
+ [Convert a license type using the License Manager console](#conversion-console)
+ [Convert a license type using the AWS CLI](#conversion-cli)
+ [Troubleshooting license type conversion](#conversion-troubleshooting)

## License type conversion limits<a name="conversion-limits"></a>

**Important**  
The use of Microsoft software is subject to the licensing terms of Microsoft\. You are responsible for complying with Microsoft licensing terms\. This documentation is provided for convenience, and you are not entitled to rely on its description\. This documentation does not constitute legal advice\. If you have questions about your licensing rights to Microsoft software, consult with your legal team, Microsoft, or your Microsoft reseller\.

License Manager restricts the types of license conversion tasks that you can create in accordance with the Microsoft Service Provider License Agreement \(SPLA\)\. Some of the restrictions that license type conversion is subject to are listed as follows\. This is not a comprehensive list and is subject to change\.
+ The Amazon EC2 instance must be launched from your own virtual machine \(VM\) image\.
+ license included SQL Server cannot be run on a Dedicated Host\.
+ A license included SQL Server instance must have at least 4 vCPUs\.

## Convert a license type using the License Manager console<a name="conversion-console"></a>

<a name="conversion-task-proc"></a>To start a license type conversion task in the console:

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the left navigation pane, choose **License type conversion tasks** > **Create license type conversion task**\.

1. Search for instances to include in the conversion by selecting **Instance ID** or **Usage operation value**\. Select the instances whose licenses you want to convert, and then choose **Next**\.
**Note**  
Only instances that are in a stopped state and have been associated by AWS Systems Manager Inventory are displayed\.

1. Select the **Usage operation value** for the license type that you are converting to\.

1. Verify your conversion task configuration\. When you are satisfied with the configuration, choose **Start conversion**\.

1. View the status of your license conversion tasks from the **License type conversion task** panel\. The **Conversion status** column displays the status of the conversion as `In progress`, `Completed`, or `Failed`\.

**Important**  
If you convert Windows Server from license included to BYOL, you must activate Windows according to your Microsoft license agreement\. See [Convert Windows Server from license included to BYOL](#convert-to-byol) for more information\.

## Convert a license type using the AWS CLI<a name="conversion-cli"></a>

To start a license type conversion task in the AWS CLI:

**Determine the license type of your instance**

1. Verify that you have installed and set up the AWS CLI\. For more information, see [Installing, updating, and uninstalling the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) and [Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)\.
**Important**  
You might need to update the AWS CLI to run certain commands and receive all required output in the following steps\.

1. Verify that you have permissions to run the `create-license-conversion-task-for-resource` AWS CLI command\. For help with this, see [Example policies for License Manager](identity-access-management.md#iam-policy-examples)\.

1. To determine the license type currently associated with your instance, run the following AWS CLI command\. Replace the instance ID with the ID of the instance for which you want to determine the license type\.

   ```
   aws ec2 describe-instances --instance-ids <instance-id> --query "Reservations[*].Instances[*].{InstanceId: InstanceId, PlatformDetails: PlatformDetails, UsageOperation: UsageOperation, UsageOperationUpdateTime: UsageOperationUpdateTime}"
   ```

1. The following is an example response to the `describe-instances` command\. Note that the `UsageOperation` value is the billing information code associated with the license\. The `UsageOperationUpdateTime` is the time when the billing code was updated\. For more information, see [DescribeInstances](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeInstances.html) in the *Amazon EC2 API reference*\.

   ```
   "InstanceId": "<instance-id>",
   "Platform details": "Windows with SQL Server Enterprise",
   "UsageOperation": "RunInstances:0800",
   "UsageOperationUpdateTime: "2021-08-16T21:16:16.000Z"
   ```

**Note**  
The usage operation for Windows Server with SQL Server Enterprise BYOL is the same as the usage operation for Windows BYOL because they are identically billed\.<a name="convert-to-byol"></a>

**Convert Windows Server from license included to BYOL**

When you convert Windows Server from license included to BYOL, License Manager does not automatically activate Windows\. You must switch the KMS server for your instance from the AWS KMS server to your own KMS server\.
**Important**  
In order to convert from license included to BYOL, the original Amazon EC2 instance must be launched from your own virtual machine \(VM\) image\. For more information about converting a VM to Amazon EC2, see [VM Import/Export](https://docs.aws.amazon.com/vm-import/latest/userguide/vmimport-image-import.html#import-vm-image)\. Instances that were originally launched from an Amazon Machine Image \(AMI\) are not eligible for license conversion to BYOL\.

Check your Microsoft license agreement to determine what methods you can use to activate Microsoft Windows Server\. For example, if you are using a KMS server, you must obtain the address of your KMS server from the original BYOL configuration of the instance\.

1. To convert the license type of your instance, run the following command, replacing the ARN with the ARN of the instance you want to convert\.

   ```
   aws license-manager create-license-conversion-task-for-resource \
       --resource-arn <instance_arn> \
       --source-license-context UsageOperation=RunInstances:0002 \
       --destination-license-context UsageOperation=RunInstances:0800
   ```

1. To activate Windows after you convert your license, you must point the Windows Server KMS server for your operating system to your own KMS servers\. Log in to the Windows instance and run the following command\. 

   ```
   slmgr.vbs /skms <your-kms-address>
   ```

**Convert Windows Server from BYOL to license included**  
When you convert Windows Server from BYOL to license included, License Manager automatically switches the KMS server for your instance to the AWS KMS server\. 

To convert the license type of your instance from BYOL to license included, run the following command, replacing the ARN with the ARN of the instance you want to convert\.

```
aws license-manager create-license-conversion-task-for-resource \
    --resource-arn <instance_arn> \
    --source-license-context UsageOperation=RunInstances:0800 \
    --destination-license-context UsageOperation=RunInstances:0002
```

**Convert Windows Server from license included to BYOL and SQL Server Standard from BYOL to license included**  
You can switch multiple products at the same time, and in multiple directions\. For example, you can convert both Windows Server and SQL Server in one license type conversion task\.

To convert the license type of your Windows Server instance from license included to BYOL, and SQL Server Standard from BYOL to license included, run the following command, replacing the ARN with the ARN of the instance you want to convert\.

```
aws license-manager create-license-conversion-task-for-resource \
    --resource-arn <instance_arn> \
    --source-license-context UsageOperation=RunInstances:0002 \
    --destination-license-context UsageOperation=RunInstances:0804
```

## Troubleshooting license type conversion<a name="conversion-troubleshooting"></a>

**Incomplete license type conversion tasks**  
License type conversion tasks contain multiple steps\. In some cases, when you convert Windows Server instances from BYOL to license included, the billing products on an instance are successfully updated\. However, the KMS server might not switch to the AWS KMS server\.

To remediate this issue, follow the steps in [Why did Windows activation fail on my EC2 Windows instance?](http://aws.amazon.com/premiumsupport/knowledge-center/windows-activation-fails/) to activate Windows either with the Systems Manager [AWSSupport\-ActivateWindowsWithAmazonLicense](https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-activatewindowswithamazonlicense.html) Automation runbook, or log in to the instance and manually make the switch to the AWS KMS server\.