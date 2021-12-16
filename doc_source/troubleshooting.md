# Troubleshooting AWS License Manager<a name="troubleshooting"></a>

The following information can help you troubleshoot issues when using AWS License Manager\. Before you start, confirm that your License Manager setup meets the requirements stated in [Settings in License Manager](settings.md)\.

## Cross\-account discovery error<a name="issue1"></a>

While setting up cross\-account discovery, you may encounter the following error message on the **Search Inventory** page: 

*Athena Exception: Athena Query failed because \- Insufficient permissions to execute the query\. Please migrate your Catalog to enable access to this database\.* 

This can occur if your Athena service uses the Athena\-managed data catalog rather than the AWS Glue Data Catalog\. For upgrade instructions, see [Upgrading to the AWS Glue Data Catalog Step\-by\-Step](https://docs.aws.amazon.com/athena/latest/ug/glue-upgrade.html)\.

## Master account cannot disassociate resources from a license Configuration<a name="issue3"></a>

If a member account of an Organization deletes the `AWSServiceRoleForAWSLicenseManagerMemberAccountRole` Service Linked Role \(SLR\) in its account, and there are member\-owned resources associated with a license configuration, the management account is prevented from disassociating licenses from those member\-account resources\. This means that the member account resources will continue to consume licenses from the management account pool\. To allow the management account to disassociate resources, restore the SLR\.

This behavior accounts for cases when a customer prefers not to allow the management account to perform some actions affecting member\-account resources\.

## Systems Manager Inventory is out of date<a name="stale-inventory"></a>

Systems Manager stores data in its Inventory data for 30 days\. During this period, License Manager counts a managed instance as active even if it is not pingable\. After inventory data has been purged from Systems Manager, License Manager marks the instance as inactive and updates local inventory data\. To keep managed instance counts accurate, we recommend manually deregistering instances in Systems Manager so that License Manager can run cleanup operations\.

## Apparent persistence of a de\-registered AMI<a name="deregistered_ami"></a>

License Manager purges stale associations between resources and license configurations once every few hours\. If an AMI associated with a license configuration is deregistered through Amazon EC2, The AMI may briefly continue to appear in the License Manager resource inventory before being purged\.

## New child account instances are slow to appear in resource inventory<a name="inventory_delay_1"></a>

When cross\-account support is enabled, License Manager updates customer accounts at 1 PM daily by default\. Instances added later in the day show up in the management account resource inventory on the following day\. You can change the frequency at which the update script runs by editing the `LicenseManagerResourceSynDataProcessJobTrigger` in the AWS Glue console for the management account\.

## After enabling cross\-account mode, child account instances are slow to appear<a name="inventory_delay_2"></a>

When you enable cross\-account mode in License Manager, instances in child accounts may take anywhere from a few minutes to a few hours to appear in the resource inventory\. The time depends on the number of child accounts and the number of instances in each child account\. 

## Cross\-account discovery cannot be disabled<a name="cross_account-permanent"></a>

After an account is configured for cross\-account discovery, it is impossible to revert to single\-account discovery\.

## Child account user cannot associate shared license configuration with an instance<a name="associating_child_account"></a>

When this occurs and cross\-account discovery has been enabled, check for the following:
+ The child account has been removed from the organization\.
+ The child account has been removed from the resource share created in the management account\.
+ The license configuration has been removed from the resource share\.

## Linking AWS Organizations accounts fails<a name="organizations_blocked"></a>

If the **Settings** page reports this error, it means that an account is not a member of an organization for the following reasons:
+ A child account was removed from the organization\.
+ A customer turned off access to License Manager from organization console of the management account\.