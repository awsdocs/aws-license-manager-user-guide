# Troubleshooting license type conversion<a name="conversion-troubleshooting"></a>

**Incomplete license type conversion tasks**  
License type conversion tasks contain multiple steps\. In some cases, when you convert Windows Server instances from BYOL to license included, the billing products on an instance are successfully updated\. However, the KMS server might not switch to the AWS KMS server\.

To remediate this issue, follow the steps in [Why did Windows activation fail on my EC2 Windows instance?](http://aws.amazon.com/premiumsupport/knowledge-center/windows-activation-fails/) to activate Windows either with the Systems Manager [AWSSupport\-ActivateWindowsWithAmazonLicense](https://docs.aws.amazon.com/systems-manager-automation-runbooks/latest/userguide/automation-awssupport-activatewindowswithamazonlicense.html) Automation runbook, or log in to the instance and manually make the switch to the AWS KMS server\.