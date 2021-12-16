# Removing Dedicated Hosts from a host resource group<a name="remove-hosts"></a>

When you remove a host from the host resource group, the instance running on the host remains on the host\. The instances attached to the host resource group remain associated with the group, and instances directly attached to the host through affinity maintain the same property\. If you share the host resource group with other AWS accounts, License Manager automatically removes the shared host and consumers receive an eviction notice to move their instances from the host in 15 days\.

Use the following steps to remove a Dedicated Host to a host resource group:

1. Log into the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Host Resource Groups**\.

1. Click on the name of the host resource that you want to remove a Dedicated Host\.

1. Choose **Dedicated Hosts**\.

1. Choose the Dedicated Host to delete from the host resource group\. Or, you can search for a Dedicated Host by host ID, host type, host state, or availability zone\.

1. Choose **Remove**\.

1. Choose **Remove** again to confirm\.