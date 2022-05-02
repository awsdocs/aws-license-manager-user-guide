# License type conversions in License Manager<a name="license-conversion"></a>

You can change your license type between AWS provided licensing and Bring Your Own License model \(BYOL\) as your business needs change, without redeploying your existing workloads\. 

You can optimize your license inventory for the following scenarios using license type conversion:

**Migrate on\-premises workloads to Amazon EC2**  
During your migration, you can deploy your workload to Amazon EC2 and use AWS provided licenses\. When the migration is complete, use License Manager license type conversion to change the license type of your instances to BYOL so that you can use the licenses that were released during the migration\.

**Continue running workloads with expiring license agreements**  
If your license agreement with Microsoft is about to expire and you do not plan to renew it, you can use License Manager license type conversion to switch from BYOL to AWS provided licenses\. This switch allows you to continue running your workloads with fully compliant software licenses provided by AWS with a flexible pay\-as\-you go licensing model\.

**Optimize costs**  
For small or irregular workloads, AWS provided licenses \(license included\) instances might be more cost effective than running BYOL because BYOL might require a longer term commitment\. For this case, you can use License Manager license type conversion to switch your instances to license included to optimize licensing related costs\. Additionally, when your workload is more steady or predictable, you can easily switch back to BYOL and use licensed media acquired directly from your software vendor if your instances were launched from your own virtual machine \(VM\) image\.

**Topics**
+ [Eligible license types for license type conversion](conversion-types.md)
+ [Prerequisites](conversion-prerequisites.md)
+ [Convert a license type](conversion-procedures.md)
+ [Tenancy conversion](conversion-tenancy.md)