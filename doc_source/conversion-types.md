# Eligible license types for license type conversion<a name="conversion-types"></a>

License type conversion is available for Windows Server and SQL Server licenses\. 

**Important**  
Instances that were originally launched from an Amazon provided Amazon Machine Image \(AMI\) are not eligible for license type conversion to BYOL\.

**Supported SQL Server editions:**
+ SQL Server Standard edition
+ SQL Server Enterprise edition
+ SQL Server Web edition

A conversion task changes the usage operation value associated with your instance\. Usage operation values for each supported platform are provided in the following table\. For more information, see [AMI billing information fields](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/billing-info-fields.html)\.


|  Platform details  |  Usage operation  | 
| --- | --- | 
|  Windows Server as BYOL  |  RunInstances:0800  | 
|  Windows Server as BYOL SQL Server \(any edition\) as BYOL  | RunInstances:0800 | 
|  Windows Server as license included  |  RunInstances:0002  | 
|  Windows Server as license included SQL Server \(any edition\) as BYOL  | RunInstances:0002 | 
|  Windows Server as license included SQL Server Web as license included  | RunInstances:0202 | 
|  Windows Server as license included SQL Server Standard as license included  |  RunInstances:0006  | 
|  Windows Server as license included SQL Server Enterprise as license included  | RunInstances:0102 | 

The following table confirms which media can be used on which instance licensing models\.


|  Source  |  Target  | 
| --- |--- |
|  | BYOL | license included | 
| --- |--- |--- |
| AWS provided Windows Server image | No | Yes | 
| AWS provided SQL Server image | No | Yes | 
| Your Windows Server media ¹ | Yes | Yes | 
| Your SQL Server media ² | Yes | Yes | 

¹ Denotes that the instance was originally launched from your own imported virtual machine \(VM\)\. You can import your VM using a service such as [VM Import/Export](https://docs.aws.amazon.com/vm-import/latest/userguide/what-is-vmimport.html) or [AWS Application Migration Service](https://docs.aws.amazon.com/mgn/latest/ug/what-is-application-migration-service.html)\.

² Denotes that you have sourced your own SQL Server installation media \(\.iso, \.exe\)\.

The following table confirms if the source license model can be converted to another between BYOL and license included\.

**Important**  
Windows Server as BYOL with SQL Server as license included is an unsupported configuration\.
Conversions that are specified as "Not needed" won't change the usage operation value\.


|  Source  |  Target  | 
| --- |--- |
|  | Windows Server as BYOL | Windows Server as license included |  Windows Server as BYOL SQL Server as BYOL  |  Windows Server as license included SQL Server as BYOL  |  Windows Server as BYOL SQL Server as license included  |  Windows Server as license included SQL Server as license included  | 
| --- |--- |--- |--- |--- |--- |--- |
| Windows Server as BYOL \(your media\) | Not needed | Yes | Not needed | Yes † | Unsupported | Yes † | 
| Windows Server as license included \(your media\) | Yes \* | Not needed | Yes \* † | Not needed ▽  | Unsupported | Yes † | 
| Windows Server as license included \(AWS provided image\) | No ✗ | Not needed | No ✗ | Not needed ▽  | Unsupported | Yes † | 
|  Windows Server as BYOL \(your media\) SQL Server as BYOL \(your media\)  | Not needed ⧫ | Yes | Not needed | Yes | Unsupported | Yes | 
|  Windows Server as license included \(your media\) SQL Server as BYOL \(your media\)  | Yes \* | Not needed ⧫ | Yes \* | Not needed | Unsupported | Yes | 
|  Windows Server as license included \(AWS provided image\) SQL Server as BYOL \(your media\)  | No ✗ | Not needed ⧫ | No ✗ | Not needed | Unsupported | Yes | 
|  Windows Server as BYOL \(your media\) SQL Server as license included  | Unsupported | Unsupported | Unsupported | Unsupported | Unsupported | Unsupported | 
|  Windows Server as license included \(AWS provided image or your media\) SQL Server as license included \(AWS provided image\)  | No ✗ | No ✗ | No ✗ | No ✗ | Unsupported | Not needed | 
|  Windows Server as license included \(your media\) SQL Server as license included \(your media\)  | Yes \* ‡ ♣ | Yes ‡ | Yes \* | Yes | Unsupported | Not needed | 
|  Windows Server as license included \(AWS provided image\) SQL Server as license included \(your media\)  | No ✗ | Yes ‡ | No ✗ | Yes | Unsupported | Not needed | 

✗ You must deploy a new instance with an alternate configuration, as converting to the target license type\(s\) is not supported\. Refer to the [media compatibility table](#media-compatibility-table) on this page for more information\.

For other conversion scenarios, you might need to take the following steps to perform a license conversion:

\* You must first modify your Windows configuration to [use your own KMS server](https://docs.aws.amazon.com/license-manager/latest/userguide/conversion-procedures.html#convert-to-byol) for license activation\.

‡ You must first **uninstall** SQL Server before converting to license included SQL Server\.

♣ You must first perform the steps for \* and ‡\. Once these steps are complete, you must convert the license type to Windows Server as license included, and then convert the license type once more to Windows Server as BYOL\.

† You must first **install** SQL Server before converting to BYOL for SQL Server\.

⧫ You must first **uninstall** SQL Server when you convert from a source with SQL Server to a target without SQL Server \(regardless of the SQL Server license type\)\.

▽ You must first **install** SQL Server when you convert from a source without SQL Server to a target with SQL Server \(regardless of the SQL Server license type\)\.