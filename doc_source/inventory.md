# Resource inventory in License Manager<a name="inventory"></a>

License Manager allows you to discover on\-premises applications using [Systems Manager inventory](http://aws.amazon.com/systems-manager/faq/), and then to attach licensing rules to them\. After licensing rules are attached to these servers, you can track them along with your AWS servers in the License Manager dashboard\.

License Manager cannot, however, validate licensing rules for these servers at launch or termination time\. To keep information about non\-AWS servers up\-to\-date, you must periodically refresh the inventory information using the **Search inventory** section of the License Manager console\.

Systems Manager stores data in its Inventory data for 30 days\. During this period, License Manager counts a managed instance as active even if it is not pingable\. After inventory data has been purged from Systems Manager, License Manager marks the instance as inactive and updates local inventory data\. To keep managed instance counts accurate, we recommend manually deregistering instances in Systems Manager so that License Manager can run cleanup operations\. 

Querying Systems Manager inventory requires a Resource Data Sync to store inventory in an Amazon S3 bucket, Amazon Athena to aggregate inventory data from organizational accounts, and AWS Glue to provide a fast query experience\. For more information, see [Using service\-linked roles for AWS License Manager](using-service-linked-roles.md)\.

Resource inventory tracking is also useful if your organization does not restrict AWS users from creating AMI\-derived instances or installing additional software on running instances\. License Manager provides you with a mechanism to easily discover these instances and applications using inventory search\. You can attach rules to these discovered resources and track and validate them the same as instances created from managed AMIs\.

**Topics**
+ [Discover resource inventory](discovery.md)
+ [Automated discovery of resource inventory](automated-discovery.md)