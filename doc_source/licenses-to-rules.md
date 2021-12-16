# Build License Manager rules from vendor licenses<a name="licenses-to-rules"></a>

You can create License Manager rule sets based on the language of software vendor licenses\. The examples that follow are not intended as blueprints for actual use cases\. In any real\-world application of a license agreement, you choose among competing options depending on the architecture and licensing history of your particular on\-premises server environment\. Your options also depend on the details of your planned migration of resources to AWS\.

As much as possible, these examples are meant to be vendor\-neutral, focusing instead on generally applicable questions of hardware and software allocation\. Vendor licensing provisions interact as well with AWS requirements and limits\. The number of licenses required for an application varies according to the instance type chosen and other factors\.

**Important**  
AWS does not participate in the audit process with software vendors\. Customers are responsible for compliance and assume the responsibility of carefully understanding and capturing rules into License Manager based on their licensing agreements\.

## Example: Implementing an operating system license<a name="os1-case"></a>

This example involves a license for a server operating system\. The licensing language imposes constraints on the type of CPU core, tenancy, and minimum number of licenses per server\. 

In this example, the licensing terms include the following stipulations:
+ Physical processor cores determine the license count\.
+ The number of licenses must equal the number of cores\. 
+ A server must run a minimum of eight cores\.
+ The operating system must run on a non\-virtualized host\.

In addition, the customer has made the following decisions:
+ Licenses for 96 cores have been purchased\.
+ A hard limit is imposed to restrict license consumption to the quantity purchased\.
+ Each server needs a maximum of 16 cores\.

The following table associates the License Manager rule\-making parameters with the vendor licensing requirements that they capture and automate\. The example values are for illustration purposes only; you would specify the values that you need in your own license configurations\.


| License Manager Rule | Settings | 
| --- | --- | 
| License counting type |  **License Type** is set to **Cores**\.  | 
| License count |  **Number of cores** is set to **96**\.  | 
| Minimum / Maximum vCPUs or cores |  **Minimum cores** is set to **8**\. **Maximum cores** is set to **16**\.  | 
| License count hard limit |  **Enforce license limit** is selected\.  | 
| Allowed tenancy |  **Tenancy** is set to **Dedicated Host**\.  | 