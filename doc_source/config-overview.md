# License configuration parameters and rules<a name="config-overview"></a>

A license configuration consists of basic parameters and rules that vary according to the parameter values\. You can also add tags to your license configurations\. After you create a license configuration, an administrator can modify the number of licenses and the usage limit to reflect changing resource needs\.

Available parameters and rules include the following:
+ **Name** — The name of the license configuration\.
+ **Description** — A description of the license configuration\.
+ **License counting type** — The metric used to count licenses\. Supported values are physical core, vCPU, socket, and instance\.
+ **\(Optional\) License count** — The number of licenses managed by this configuration\.
+ **\(Optional\) License count hard limit** — The kind of limit represented by the license count\. A hard limit blocks the launch of an out\-of\-compliance instance\. A soft limit permits out\-of\-compliance launches but sends an alert when one occurs\. 
+ **Number of licenses consumed** \- The number of licenses used by a resource\.
+ **Status** — Indicates whether the configuration is active\.
+ **Product information** — The names and versions of the products for [automated discovery](automated-discovery.md)\. The supported products are Windows Server, SQL Server, and Oracle Database\.
+ **\(Optional\) Rules** \- These include the following\. Available rules vary by counting type\.
  + **License affinity to host \(in days\)** — Restricts license usage to the host for the specified number of days\. The range is 1 to 180\. The counting type must be Cores or Sockets\. After the affinity period elapses, the license will be available for reuse within 24 hours\.
  + **Maximum cores** — Maximum count cores for a resource\.
  + **Maximum sockets** — Maximum count sockets for a resource\.
  + **Maximum vCPUs** — Maximum count vCPUs for a resource\.
  + **Minimum cores** — Minimum count cores for a resource\.
  + **Minimum sockets** — Minimum count sockets for a resource\.
  + **Minimum vCPUs** — Minimum count vCPUs for a resource\.
  + **Tenancy** — Restricts license usage to the specified EC2 tenancy\. Dedicated Hosts are required if the counting type is Cores or Sockets\. Shared tenancy, Dedicated Hosts, and Dedicated Instances are supported if the counting type is Instances or vCPUs\. The console \(and API\) names are as follows:
    + **Shared** \(`EC2-Default`\)
    + **Dedicated Instance** \(`EC2-DedicatedInstance`\)
    + **Dedicated Host** \(`EC2-DedicatedHost`\)
  + **vCPU Optimization** — License Manager integrates with [CPU optimization](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-optimize-cpu.html) support in Amazon EC2, which enables you to customize the number of vCPUs on an instance\. If this rule is set to True, License Manager counts vCPUs based on the customized core and thread count\. Otherwise, License Manager counts the default number of vCPUs for the instance type\.

The following table describes which license rules are available for each counting type\.


| Console name | API name | Cores | Instances | Sockets | vCPUs | 
| --- | --- | --- | --- | --- | --- | 
| **License affinity to host \(in days\)** | licenseAffinityToHost | ♦ |  | ♦ |  | 
| **Maximum cores** | maximumCores | ♦ | ♦ |  |  | 
| **Maximum sockets** | maximumSockets |  | ♦ | ♦ |  | 
| **Maximum vCPUs** | maximumVcpus |  | ♦ |  | ♦ | 
| **Minimum cores** | minimumCores | ♦ | ♦ |  |  | 
| **Minimum sockets** | minimumSockets |  | ♦ | ♦ |  | 
| **Minimum vCPUs** | minimumVcpus |  | ♦ |  | ♦ | 
| **Tenancy** | allowedTenancy | ♦ | ♦ | ♦ | ♦ | 
| **vCPU Optimization** | honorVcpuOptimization |  |  |  | ♦ | 