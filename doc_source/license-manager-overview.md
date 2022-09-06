# How License Manager works<a name="license-manager-overview"></a>

Effective software license management relies on the following:
+ An expert understanding of language in enterprise licensing agreements
+ Appropriately restricted access to operations that consume licenses
+ Accurate tracking of license inventory 

Enterprises are likely to have dedicated persons or teams responsible for each of these domains\. It then becomes a problem of effective communication, particularly between license experts and system administrators\. License Manager provides a way of pooling knowledge from various domains\. Crucially, it also integrates natively with AWS services—for example, with the Amazon EC2 control plane where instances are created and deleted\. This means that License Manager rules and limits capture business and operational knowledge, and also translate to automated controls on instance creation and application deployment\. 

The following diagram illustrates the distinct but coordinated duties of license administrators, who manage permissions and configure License Manager, and users, who create, manage, and delete resources through the Amazon EC2 console\.

![\[License Manager workflow\]](http://docs.aws.amazon.com/license-manager/latest/userguide/images/process.png)

If you are responsible for managing licenses in your organization, you can use License Manager to set up licensing rules, attach them to your launches, and keep track of usage\. The users in your organization can then add and remove license\-consuming resources without additional work\.

A licensing expert manages licenses across the entire organization, determining resource inventory needs, supervising license procurement, and driving compliant license usage\. In an enterprise using License Manager, this work is consolidated through the License Manager console\. As shown in the diagram, this involves setting service permissions, creating self\-managed licenses, taking inventory of computing resources both on\-premises and in the cloud, and associating self\-managed licenses with discovered resources\. In practice, this could mean associating a self\-managed license with an approved Amazon Machine Image \(AMI\) that IT uses as a template for all Amazon EC2 instance deployments\.

License Manager saves costs that would otherwise be lost to license violations\. While internal audits reveal violations only after the fact, when it is too late to avoid penalties for non\-compliance, License Manager prevents expensive incidents from ever occurring\. License Manager simplifies reporting with built\-in dashboards showing license consumption and resources tracked\.