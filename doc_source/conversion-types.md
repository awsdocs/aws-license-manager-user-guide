# Eligible license types for license type conversion<a name="conversion-types"></a>

License type conversion is available for Windows Server and SQL Server licenses\. 

**Supported SQL Server editions:**
+ SQL Server Standard edition
+ SQL Server Enterprise edition
+ SQL Server Web edition

A conversion task changes the usage operation value associated with your instance\. Usage operation values for each supported platform are provided in the following table\. For more information, see [AMI billing information fields](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/billing-info-fields.html)\.


|  Platform details  |  Usage operation  | 
| --- | --- | 
|  Windows Server License Included  |  RunInstances:0002  | 
|  Windows Server BYOL  |  RunInstances:0800  | 
|  Windows Server License Included with SQL Server Standard License Included  |  RunInstances:0006  | 
| Windows Server License Included with SQL Server Enterprise License Included | RunInstances:0102 | 
| Windows Server License Included with SQL Server Web License Included | RunInstances:0202 | 
| Windows Server License Included with SQL Server \(any edition\) BYOL | RunInstances:0002 | 
| Windows Server BYOL with SQL Server \(any edition\) BYOL | RunInstances:0800 | 