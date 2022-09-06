# Terminating EC2 instances providing user\-based subscriptions<a name="user-based-subscriptions-terminate-instances"></a>

You can delete an instance providing a user\-based subscription if you no longer need it\. This is referred to as terminating the instance\. You should first disassociate all users from the instance, and then terminate the instance from the Amazon EC2 console\.

**Note**  
Users must be disassociated from the instance in order to stop incurring charges for the subscription\. For more information, see [Disassociating users from user\-based subscriptions](user-based-subscriptions-disassociate-users.md)\.

**To identify and terminate instances providing user\-based subscriptions**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **User association**\.

1. On the **User association** page, choose the instance ID to access instance’s details page\.

1. Make note of the instance ID as you will need it to terminate the instance\.

1. Disassociate all users from the instance\.

1. Follow the steps listed in [Terminate an instance](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/terminating-instances.html#terminating-instances-console)\.