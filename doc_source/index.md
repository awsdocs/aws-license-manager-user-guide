# AWS License Manager User Guide

-----
*****Copyright &copy; Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in
connection with any product or service that is not Amazon's,
in any manner that is likely to cause confusion among customers,
or in any manner that disparages or discredits Amazon. All other
trademarks not owned by Amazon are the property of their respective
owners, who may or may not be affiliated with, connected to, or
sponsored by Amazon.

-----
## Contents
+ [What is AWS License Manager?](license-manager.md)
+ [How License Manager works](license-manager-overview.md)
+ [Getting started with AWS License Manager](getting-started.md)
+ [Working with AWS License Manager](using-license-manager.md)
   + [Self-managed licenses in License Manager](license-configurations.md)
      + [Self-managed license parameters and rules](config-overview.md)
      + [Build License Manager rules from vendor licenses](licenses-to-rules.md)
      + [Create a self-managed license](create-license-configuration.md)
      + [Share a self-managed license](share-license-configuration.md)
      + [Edit a self-managed license](modify-license-configuration.md)
      + [Deactivate a self-managed license](deactivate-license-configuration.md)
      + [Delete a self-managed license](delete-license-configuration.md)
   + [License rules in License Manager](license-rules.md)
   + [Usage reports in License Manager](license-reporting.md)
   + [License type conversions in License Manager](license-conversion.md)
      + [Eligible license types for license type conversion](conversion-types.md)
      + [Prerequisites](conversion-prerequisites.md)
      + [Convert a license type](conversion-procedures.md)
      + [Tenancy conversion](conversion-tenancy.md)
   + [Host resource groups in AWS License Manager](host-resource-groups.md)
      + [Adding Dedicated Hosts to a host resource group](add-hosts.md)
      + [Removing Dedicated Hosts from a host resource group](remove-hosts.md)
   + [Inventory search in License Manager](inventory.md)
      + [Working with inventory search](discovery.md)
      + [Automated discovery of inventory](automated-discovery.md)
   + [Granted licenses in License Manager](granted-licenses.md)
   + [Seller issued licenses in AWS License Manager](seller-issued-licenses.md)
   + [User-based subscriptions in AWS License Manager](user-based-subscriptions.md)
      + [Supported software for user-based subscriptions](user-based-subscriptions-supported-software.md)
      + [Considerations](user-based-subscriptions-considerations.md)
      + [Prerequisites](user-based-subscriptions-prerequisites.md)
      + [Getting started with user-based subscriptions](user-based-subscriptions-getting-started.md)
      + [Modifying directory settings for user-based subscriptions](user-based-subscriptions-modify-ad.md)
      + [Modifying VPC settings for user-based subscriptions](user-based-subscriptions-modify-vpc.md)
      + [Disassociating users from user-based subscriptions](user-based-subscriptions-disassociate-users.md)
      + [Unsubscribing users from user-based subscriptions](user-based-subscriptions-unsubscribe-users.md)
      + [Terminating EC2 instances providing user-based subscriptions](user-based-subscriptions-terminate-instances.md)
      + [Removing a directory for user-based subscriptions](user-based-subscriptions-remove-ad.md)
      + [Troubleshooting user-based subscriptions](user-based-subscriptions-troubleshoot.md)
   + [Register a delegated administrator](delegated-administrator.md)
   + [Settings in License Manager](settings.md)
   + [Dashboard in AWS License Manager](dashboard.md)
+ [Security in AWS License Manager](security.md)
   + [Data protection in AWS License Manager](data-protection.md)
   + [Identity and access management for AWS License Manager](identity-access-management.md)
   + [Using service-linked roles for AWS License Manager](using-service-linked-roles.md)
      + [License Manager – Core role](license-manager-role-core.md)
      + [License Manager – Management account role](management-role.md)
      + [License Manager – Member account role](member-role.md)
      + [License Manager – User-based subscription role](user-based-subscription-role.md)
   + [AWS managed policies for AWS License Manager](security-iam-awsmanpol.md)
   + [Cryptographic Signing of Licenses](license-signing.md)
   + [Compliance validation for AWS License Manager](compliance-validation.md)
   + [Resilience in AWS License Manager](disaster-recovery-resiliency.md)
   + [Infrastructure security in AWS License Manager](infrastructure-security.md)
   + [AWS License Manager and interface VPC endpoints (AWS PrivateLink)](interface-vpc-endpoints.md)
+ [Troubleshooting AWS License Manager](troubleshooting.md)
+ [Logging AWS License Manager API calls using AWS CloudTrail](logging-using-cloudtrail.md)
+ [Document history for AWS License Manager](doc-history.md)