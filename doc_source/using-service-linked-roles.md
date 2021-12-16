# Using service\-linked roles for AWS License Manager<a name="using-service-linked-roles"></a>

AWS License Manager uses AWS Identity and Access Management \(IAM\)[ service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to License Manager\. Service\-linked roles are predefined by License Manager and include all the permissions that the service requires to call other AWS services on your behalf\. 

A service\-linked role makes setting up License Manager easier because you don’t have to manually add the necessary permissions\. License Manager defines the permissions of its service\-linked roles, and unless defined otherwise, only License Manager can assume its roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

You can delete a service\-linked role only after first deleting the related resources\. This protects your License Manager resources because you can't inadvertently remove permissions to access the resources\.

License Manager actions depend on three service\-linked roles, as described in the following sections\.

**Topics**
+ [Core role](license-manager-role-core.md)
+ [Management account role](management-role.md)
+ [Member account role](member-role.md)