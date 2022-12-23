# Troubleshooting user\-based subscriptions<a name="user-based-subscriptions-troubleshoot"></a>

The following are troubleshooting tips to help solve issues that can occur with user\-based subscriptions in AWS License Manager\.

**Contents**
+ [Troubleshooting instance compliance](#user-based-subscriptions-troubleshoot-instance-compliance)
+ [Troubleshooting license compliance](#user-based-subscriptions-troubleshoot-license-compliance)
+ [Troubleshooting instance connectivity](#user-based-subscriptions-troubleshoot-instance-connectivity)
+ [Troubleshooting failures to join the domain](#user-based-subscriptions-troubleshoot-domain-join)
+ [Troubleshooting Systems Manager connectivity](#user-based-subscriptions-troubleshoot-systems-manager-connectivity)
+ [Troubleshooting Systems Manager Run Command](#user-based-subscriptions-troubleshoot-systems-manager-commands)

## Troubleshooting instance compliance<a name="user-based-subscriptions-troubleshoot-instance-compliance"></a>

Instances providing user\-based subscriptions must remain in a healthy status to be in compliance\. Instances that are marked as unhealthy no longer meet the required prerequisites\. License Manager will attempt to return the instance to a healthy status, but instances that are not able to return to a healthy status are terminated\.

Instances which are launched to provide user\-based subscriptions and are unable to complete the initial configuration will be terminated\. You must correct the configuration issue and launch new instances to provide user\-based subscriptions in this scenario\. For more information, see the [Prerequisites](user-based-subscriptions-prerequisites.md)\.

## Troubleshooting license compliance<a name="user-based-subscriptions-troubleshoot-license-compliance"></a>

If you configured your directory to provide user\-based subscriptions with Microsoft Office, you must ensure your resources can connect to the VPC endpoints License Manager creates\. The endpoints require inbound traffic on TCP port 1688 from the instances providing user\-based subscriptions\.

You can use [Reachability Analyzer](https://docs.aws.amazon.com/vpc/latest/reachability/what-is-reachability-analyzer.html) to help confirm that the networking configuration from your instances providing user\-based subscriptions and the VPC endpoints are configured properly\. You can specify an instance ID launched in a subnet providing user\-based subscriptions as the source, and a VPC endpoint provisioned for Microsoft Office products as the destination\. Specify TCP as the protocol and 1688 for the destination port for the path to analyze\. For more information, see [How can I troubleshoot connectivity issues over my gateway and interface VPC endpoints?](http://aws.amazon.com/premiumsupport/knowledge-center/vpc-fix-gateway-or-interface-endpoint/)\.

## Troubleshooting instance connectivity<a name="user-based-subscriptions-troubleshoot-instance-connectivity"></a>

Users must be able to use RDP to connect to the instances providing user\-based subscriptions in order to utilize the products within\. For more information on troubleshooting instance connectivity, see [Troubleshoot connecting to your Windows instance](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/troubleshoot-connect-windows-instance.html) in the *Amazon EC2 User Guide for Windows Instances*\.

## Troubleshooting failures to join the domain<a name="user-based-subscriptions-troubleshoot-domain-join"></a>

Users must be able to connect to the instances providing the user\-based subscription products with their user identities from the directory configured in the License Manager settings\. Instances that fail to join the domain will be terminated\.

To troubleshoot, you may need to launch an instance and [manually join the domain](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/join_windows_instance.html) so that the resource is not terminated before you can investigate\. The instance must receive and execute the Systems Manager Run Command successfully, and the instance must also be able to complete the domain join within the operating system\. For more information, see [Understanding command statuses](https://docs.aws.amazon.com/systems-manager/latest/userguide/monitor-commands.html) in the *AWS Systems Manager User Guide* and [How to troubleshoot errors that occur when you join Windows\-based computers to a domain](https://docs.microsoft.com/en-US/troubleshoot/windows-server/identity/troubleshoot-errors-join-computer-to-domain) on the Microsoft website\.

## Troubleshooting Systems Manager connectivity<a name="user-based-subscriptions-troubleshoot-systems-manager-connectivity"></a>

Instances that provide user\-based subscriptions must be managed by AWS Systems Manager or they will be terminated\. For more information, see [Troubleshooting SSM Agent](https://docs.aws.amazon.com/systems-manager/latest/userguide/troubleshooting-ssm-agent.html) and [Troubleshooting managed node availability](https://docs.aws.amazon.com/systems-manager/latest/userguide/troubleshooting-managed-instances.html) in the *AWS Systems Manager User Guide*\.

## Troubleshooting Systems Manager Run Command<a name="user-based-subscriptions-troubleshoot-systems-manager-commands"></a>

Run Command, a capability of Systems Manager, is used with instances providing user\-based subscriptions to join the domain, harden the operating system, and perform access audits for the included product\. For more information, see [Understanding command statuses](https://docs.aws.amazon.com/systems-manager/latest/userguide/monitor-commands.html) in the *AWS Systems Manager User Guide*\.