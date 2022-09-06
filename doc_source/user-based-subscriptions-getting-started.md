# Getting started with user\-based subscriptions<a name="user-based-subscriptions-getting-started"></a>

The following steps detail how you can get started with utilizing user\-based subscriptions\. These steps assume you have already implemented the prerequisites in your environment\. For more information, see the [Prerequisites](user-based-subscriptions-prerequisites.md) section\.

**Contents**
+ [Step 1: Configure AWS Directory Service for Microsoft Active Directory](#user-based-subscriptions-configure-ad)
+ [Step 2: Subscribe to a product](#user-based-subscriptions-subscribe-products)
+ [Step 3: Launch an instance to provide user\-based subscriptions](#user-based-subscriptions-launch-instance)
+ [Step 4: Associate users to an instance](#user-based-subscriptions-associate-users)
+ [Step 5: Connect to a user\-based subscription instance](#user-based-subscriptions-connect)

## Step 1: Configure AWS Directory Service for Microsoft Active Directory<a name="user-based-subscriptions-configure-ad"></a>

License Manager requires AWS Managed Microsoft AD in order to associate the users with\. When you register your AWS Managed Microsoft AD directory, License Manager will create two Elastic Network Interfaces \(ENIs\) in order for the service to communicate with your directory with a description similar to *AWS created network interface for LicenseManager *<directory\_id>**\. For more information about creating an AWS Managed Microsoft AD directory, see the [Create your AWS Managed Microsoft AD directory](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/ms_ad_getting_started_create_directory.html) page in the *AWS Directory Service User Guide*\.

You must select all products you require for the user\-based subscriptions while configuring your directory as users can only subscribe to configured products\. If you require user\-based subscriptions in multiple AWS Regions, you will need to perform the following steps in each Region\.

**Important**  
You must allow License Manager to create the required [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) before you can proceed\. For more information, see the [Prerequisites](user-based-subscriptions-prerequisites.md) section\.

**To configure AWS Managed Microsoft AD for user\-based subscriptions \(Console\)**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. Navigate to the **Settings** page by choosing **Settings** in the left navigation pane, or by choosing **Open Settings** in the banner \.

1. On the **Settings** page, under the **AWS Managed Microsoft AD** section, choose **Configure**\.

1. For the **AWS Managed Directory Name and ID**, choose the directory that contains the users you want to create user\-based subscriptions for\.

1. For **Product Name and ID**, select any required products and then choose **Configure**\.

   After you choose **Configure**, the **AWS Managed Microsoft AD** section on the **Settings **page will display your **Directory ID** with the **Status **of **Configuring**\. Once the configuration process is complete, the **Status** will display **Configured**, and you can proceed to the remaining steps\.

**To configure AWS Managed Microsoft AD for user\-based subscriptions \(AWS CLI\)**  
You can register your AWS Managed Microsoft AD as the identity provider for user\-based subscriptions with the following command\.

```
aws license-manager-user-subscriptions register-identity-provider --product "<product-name>" --identity-provider ""ActiveDirectoryIdentityProvider" = {"DirectoryId" = "<directory_id>"}"
```

## Step 2: Subscribe to a product<a name="user-based-subscriptions-subscribe-products"></a>

**To subscribe to configured products in the AWS Marketplace**  
After you configure your directory with the required products, you may also need to subscribe to the required products\. Products with a **Marketplace Subscription Status** of **Inactive** require you to subscribe before you can associate users to an instance and utilize them\.

All users associated with instances providing user\-based subscription products must have a single active subscription to **Win Remote Desktop Services SAL** in addition to any other products they would like to use\. Microsoft Remote Desktop Services \(RDS\), known as Terminal Services in Windows Server 2008 and earlier, is one of the components of Microsoft Windows that allow a user to take control of a remote computer or virtual machine over a network connection\. RDS allow users to remotely access graphical desktops and Windows applications\. The Subscriber Access License \(SAL\) permits this RDS functionality to your users\.

You can subscribe to your products directly on the AWS Marketplace using the following links:
+ [Visual Studio Professional](http://aws.amazon.com/marketplace/pp/prodview-zo3zltrbpgr5i)
+ [Visual Studio Enterprise](http://aws.amazon.com/marketplace/pp/prodview-dzstlnjdl3izg)
+ [Win Remote Desktop Services SAL](http://aws.amazon.com/marketplace/pp/prodview-buamtl3v3xaes)

**To discover and subscribe to products from the License Manager console**

You can also discover the required products to subscribe to from the License Manager console\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **Products**\.

1. Choose a product’s name to display subscription details\.

1. Choose **View in AWS Marketplace**\.

1. Review the subscription details and choose **Continue to Subscribe**\.

1. Review the terms and choose **Accept Terms** if you want to proceed\.

If you accept the terms, the product subscription will need to be processed\. The subscription will have an in progress message until it completes\. You can repeat these steps for any other configured products you require\. Once all of the required products have an active subscription, you can proceed with subscribing users to the products\.

**Note**  
Your estimated bill for charges on the number of users and related costs will take 48 hours to appear for billing periods that haven't closed \(marked as **Pending** billing status\) in AWS Billing\. For more information, see [Viewing your monthly charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/invoice.html) in the *AWS Billing User Guide*\.

## Step 3: Launch an instance to provide user\-based subscriptions<a name="user-based-subscriptions-launch-instance"></a>

After you have subscribed to a product, you must launch instances for your users to connect to from the AWS Marketplace AMI that includes the product\. Once you launch an instance, AWS Systems Manager will attempt to join the instance to the domain and perform additional configuration and hardening on the resource\. The configurations to make the instance ready to use can take around 20 minutes to complete\. You can confirm the resource is ready to use from the **User association** page of the License Manager console by checking for a **Health status** of **Active** for the instance\.

**To launch a instance with user\-based subscriptions**

1. Access the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. Under **Images**, choose **AMI Catalog**\.

1. Choose **AWS Marketplace AMIs**\.

1. Enter **Visual Studio** into the search box and press enter\.

1. Under **Publisher**, select **Amazon Web Services**\. 

1. Choose **Select** for the product you want to launch an instance to provide\.

1. Choose **Continue** to proceed\.

1. Choose **Launch Instance with AMI**\.

1. Complete the wizard while ensuring that you:

   1. Choose a Nitro based instance that is not graviton based\.

   1. Choose a VPC and subnet from which your instance can connect to your AWS Managed Microsoft AD directory\.

   1. Choose a security group that permits connectivity from your instance to your AWS Managed Microsoft AD directory\.

   1. Expand **Advanced details** and choose an IAM role that allows Systems Manager functionality for your instance\.

1. Choose **Launch instance**\.

Once you have running instances from the AWS Marketplace AMI, you must subscribe users to the product and associate them with instances which provide the product so that they can utilize it\.

**Important**  
The instances you launch must meet the required prerequisites to be in compliance\. Resources that are unable to complete the initial configuration will be terminated\. For more information, see the [Prerequisites](user-based-subscriptions-prerequisites.md) and [Troubleshooting user\-based subscriptions](user-based-subscriptions-troubleshoot.md)\.

## Step 4: Associate users to an instance<a name="user-based-subscriptions-associate-users"></a>

Once you have subscribed to the required product’s AWS Marketplace AMI, you can subscribe users to a product and associate users with the instance launched to provide the product\. When you subscribe a user, the directory is checked to ensure the user identity is present\. One subscription will be created for each user you subscribe to the product\.

**Important**  
Each user must have a subscription to both RDS SAL and the product they will utilize\.

The **Products** page in License Manager will display active subscriptions by listing their **Marketplace subscription status** as **Active**\. In the product’s details page, License Manager will display active user subscriptions with a **Status** of **Subscribed**\.

**Important**  
If your directory is not configured with the product, a notification bar will appear at the top of the console advising you to adjust the directory’s settings\. On the notification bar, choose **Open settings** to access the **Settings** page in License Manager and configure your directory\.  
Subscribing users to a product in which the **Marketplace subscription status** is **Inactive** will fail\.

**To associate users to an instance with an active subscription**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **Products**\.

1. Select a product to subscribe users to in which the **Marketplace subscription status** is **Active**, and choose **Subscribe user**\.

1. Specify up to five user names that exist in your directory and choose **Subscribe**\.

On the **User association** page, the users you selected should be displayed under **Users** with an ** Association Status** of ** Associated**\. Also, on the **Product** page, you can review the product's details page by choosing the **Product name**\. Subscribed users will be displayed under **Users** with a **Status** of **Subscribed**\.

**To subscribe users to a product \(Console\)**
**Important**  
Before associating a product to an instance you must first subscribe users to the products\.

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **Products**\.

1. Select a product to subscribe users to in which the **Marketplace subscription** status is **Active**, and choose Subscribe user\.

1. Specify up to five user names that exist in your directory and choose **Subscribe**\.

Users that have a subscription will be displayed under **Users** with a **Status** of **Subscribed**\.

**To subscribe users to a product \(AWS CLI\)**  
You can subscribe users to a product that is registered with your identity provider using the following command\.

```
aws license-manager-user-subscriptions start-product-subscription --username <user_name> --product <product_name> --identity-provider ""ActiveDirectoryIdentityProvider" = {"DirectoryId" = "<directory_id>"}"
```

**To associate users to an instance \(Console\)**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **User association**\.

1. Select the instance you want to associate users with, then choose **Associate user**\.

1. Specify up to five user names that exist in your directory and choose **Associate**\.

Users that have been associated will be displayed under **Users** with an **Association Status** of **Associated**\.

**To associate users to an instance \(AWS CLI\)**  
You can associate users with an instance launched to provide the user\-based subscription with the following command\.

```
aws license-manager-user-subscriptions associate-user --username <user_name> --instance-id <instance_id> --identity-provider  ""ActiveDirectoryIdentityProvider" = {"DirectoryId" = "<directory_id>"}"
```

**Note**  
Your estimated bill for charges on the number of users and related costs will take 48 hours to appear for billing periods that haven't closed \(marked as **Pending** billing status\) in AWS Billing\. For more information, see [Viewing your monthly charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/invoice.html) in the *AWS Billing User Guide*\.

## Step 5: Connect to a user\-based subscription instance<a name="user-based-subscriptions-connect"></a>

Once you have associated users with the instance providing the product, they can connect to the instance if the **Health status** of the instance is **Active**\. The users will need to connect with their user credentials for the domain to utilize the product with their associated identity\.

**Important**  
The process of creating the EC2 instance and preparing it for users can take around 20 minutes\. The **Association status** of the instance must be **Active** in order to access it and utilize the product\.

**To connect to instances with a user\-based subscription**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. In the left navigation pane, under **User\-based subscriptions**, choose **User association**\.

1. On the **User association** page, confirm the instance’s **Health status** is **Active**\.

1. Make note of the instance ID as you will need it to gather connection details\.

1. Follow the steps listed in [Connect to your Windows instance using RDP](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/connecting_to_windows_instance.html#connect-rdp) while ensuring to specify the fully\-qualified user name of the associated user from AWS Managed Microsoft AD\.