# Host resource groups in AWS License Manager<a name="host-resource-groups"></a>

A [Dedicated Host](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-hosts-overview) is a physical server with EC2 instance capacity fully dedicated to your use\. A host resource group is a collection of Dedicated Hosts that you can manage as a single entity\. As you launch instances, License Manager allocates the hosts and launches instances on them based on the settings that you configured\. You can add existing Dedicated Hosts to a host resource group and take advantage of automated host management through License Manager\. 

You can use host resource groups to separate hosts by purpose, for example, development test hosts versus production, organizational unit, or license constraint\. After you add a Dedicated Host to a host resource group, you cannot launch instances directly on the Dedicated Host, you must launch them using the host resource group\.

**Settings**

You can configure the following settings for a host resource group:
+ **Allocate hosts automatically**–Indicates whether Amazon EC2 can allocate new hosts on your behalf if launching an instance in this host resource group would exceed its available capacity\.
+ **Release hosts automatically**–Indicates whether Amazon EC2 can release unused hosts on your behalf\. An unused host has no running instances\.
+ **Recover hosts automatically**–Indicates whether Amazon EC2 can move instances from a host that has failed unexpectedly to a new host\.
+ **Associated self\-managed licenses**–The self\-managed licenses that can be used to launch instances in this host resource group\.
+ **\(Optional\) Instance families**–The types of instances that you can launch\. By default, you can launch any instance types that are supported on a Dedicated Host\. If you launch [Nitro\-based](url-ec2-user;instance-types.html#ec2-nitro-instances) instances, then you can launch instances with different instance types in the same host resource group\. Otherwise, you must launch only instances with the same instance type in the same host resource group\.

**Topics**
+ [Create a host resource group](#host-resource-group-create)
+ [Share a host resource group](#host-resource-group-share)
+ [Launch an instance in a host resource group](#host-resource-group-launch)
+ [Modify a host resource group](#host-resource-group-modify)
+ [Delete a host resource group](#host-resource-group-delete)
+ [Adding Dedicated Hosts to a host resource group](add-hosts.md)
+ [Removing Dedicated Hosts from a host resource group](remove-hosts.md)

## Create a host resource group<a name="host-resource-group-create"></a>

Configure a host resource group to enable License Manager to manage your Dedicated Hosts\. To best utilize your most expensive licenses, you can associate one or more core\- or socket\-based self\-managed licenses with your host resource group\. To best optimize host utilization, you can allow all core\- or socket\-based self\-managed licenses with your host resource group\.

**To create a host resource group**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Host resource groups**\.

1. Choose **Create host resource group**\.

1. For **Host resource group details**, specify a name and description for the host resource group\.

1. For **EC2 Dedicated Host management settings**, enable or disable the following settings as needed:
   + **Allocate hosts automatically**
   + **Release hosts automatically**
   + **Recover hosts automatically**

1. \(Optional\) For **Additional settings**, select the instance families that you can launch in the host resource group\.

1. For **self\-managed licenses**, select one or more core\- or socket\-based self\-managed licenses\.

1. \(Optional\) For **Tags**, add one or more tags\.

1. Choose **Create**\.

## Share a host resource group<a name="host-resource-group-share"></a>

You can use AWS Resource Access Manager to shared your host resource groups through AWS Organizations\. After you share a host resource group and self\-managed license, member accounts can launch instances into the shared host resource group\. The new hosts are allocated in the account that owns the host resource group\. The member account owns the instances\. For more information, see the [AWS RAM User Guide](https://docs.aws.amazon.com/ram/latest/userguide/)\.

## Launch an instance in a host resource group<a name="host-resource-group-launch"></a>

When you launch an instance, you can specify a host resource group\. For example, you can use the following [run\-instances](https://docs.aws.amazon.com/cli/latest/reference/ec2/run-instances.html) command\. You must associate a core\- or socket\-based self\-managed license with the AMI\.

```
aws ec2 run-instances --min-count 2 --max-count 2 \
--instance-type c5.2xlarge --image-id ami-0abcdef1234567890 \
--placement="Tenancy=host,HostResourceGroupArn=arn"
```

You can also use the Amazon EC2 console\. For more information, see [Launching Instances into a Host Resource Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-dedicated-hosts-work.html#launching-hrg-instances) in the *Amazon EC2 User Guide*\.

## Modify a host resource group<a name="host-resource-group-modify"></a>

You can modify the settings for a host resource group at any time\. You cannot set the host limit lower than the number of existing hosts in the host resource group\. You cannot remove an instance type if there's an instance of that type running in the host resource group\.

**To modify a host resource group**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Host resource groups**\.

1. Select the host resource group and choose **Actions**, **Edit**\.

1. Modify the settings as needed\.

1. Choose **Save changes**\.

## Delete a host resource group<a name="host-resource-group-delete"></a>

You can delete a host resource group if it has no hosts\.

**To delete a host resource group**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, choose **Host resource groups**\.

1. Select the host resource group and choose **Actions**, **Delete**\.

1. When prompted for confirmation, choose **Delete**\.