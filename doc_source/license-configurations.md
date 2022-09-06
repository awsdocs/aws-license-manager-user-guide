# Self\-managed licenses in License Manager<a name="license-configurations"></a>

Self\-managed licenses are the core of License Manager\. Self\-managed licenses were formerly known as "license configurations"\. Self\-managed licenses contain licensing rules based on the terms of your enterprise agreements\. The rules that you create determine how AWS processes commands that consume licenses\. While creating self\-managed licenses, work closely with your organization's compliance team to review your enterprise agreements\.

**Limits**
+ Number of self\-managed licenses per resource: 10
+ Total number of self\-managed licenses: 25
+ Systems Manager managed instances must be associated with vCPU and instance type self\-managed licenses\.

**Topics**
+ [Parameters and rules](config-overview.md)
+ [Build rules from vendor licenses](licenses-to-rules.md)
+ [Create a self\-managed license](create-license-configuration.md)
+ [Share a self\-managed license](share-license-configuration.md)
+ [Edit a self\-managed license](modify-license-configuration.md)
+ [Deactivate a self\-managed license](deactivate-license-configuration.md)
+ [Delete a self\-managed license](delete-license-configuration.md)