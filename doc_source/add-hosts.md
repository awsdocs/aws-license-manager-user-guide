# Adding Dedicated Hosts to a host resource group<a name="add-hosts"></a>

You can add your existing hosts to a host resource group from the AWS Management Console, AWS CLI, or AWS API\. To add your hosts, you must be the AWS account owner where you created the Dedicated Host and host resource groups\. If your host resource group lists allowed self\-managed licenses and instances types, the host you add must match these requirements\. 

**Note**  
Suppose you stop the instances and want to restart them\. You must perform the following two tasks:  
 [Modify](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_ModifyInstancePlacement.html) the instance to point to the host resource group\.
[Associate](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateLicenseSpecificationsForResource.html) self\-managed licenses to match the host resource group\.

For more information about Resource Groups, see [AWS Resource Groups User Guide](https://docs.aws.amazon.com/ARG/latest/userguide/welcome.html)\.

Use the following steps to add one or more Dedicated Hosts to a resource group:

1. Log into the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Choose **Host Resource Groups**\.

1. From the list of host resource group names, click on the name of the host resource group where you want to add the Dedicated Host\.

1. Choose **Dedicated Hosts**\. 

1. Choose **Add**\.

1. Choose one or more Dedicated Hosts to add to the host resource group\. 

1. Choose **Add**\.

   Adding the host may take 1 \- 2 minutes, and then it appears in the list of **Dedicated Hosts\.**