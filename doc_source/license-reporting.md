# Usage reports in License Manager<a name="license-reporting"></a>

 Using AWS License Manager you can track the history of your self\-managed licenses by scheduling periodic snap shots of your license usage\. By setting up usage reports License Manager will automatically upload reports of your self\-managed licenses to an S3 bucket based on your specifications\. Usage reports were formerly called report generators\. You can set up multiple usage reports to effectively track configurations of different license types in your environment\. 

**Note**  
AWS License Manager does not store your reports\. License Manager reports are published directly to your S3 bucket\. Once you delete a usage report, reports are no longer published to your S3 bucket\.

## Creating a usage report<a name="create-report-generator"></a>

 When you create a usage report you specify a self\-managed license type for License Manager to track, a frequency interval that defines how often to generate reports, and a report type\. All reports are generated in CSV format and published to an S3 bucket\. A usage report can produce one or more of following report types\.

**Self\-managed license summary report**  
 This report type contains information on the number of consumed licenses and details about self\-managed license\. The tracked self\-managed license type is listed with details such as the license count, license rules, and the distribution of licenses across different resource types\.

**Resource usage report**  
This report type gives you details about your tracked resources and their license consumption\. Each tracked resource using the specified self\-managed license type is listed with details such as the license ID, the status of the resource, and the AWS account ID that owns the resource\.

**To create a usage report**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Usage reports**\.

1. Choose **Create usage report**, then from the **Create usage report** pane define the parameters for the report:

   1. Enter a **Name** and optional **Description** for your usage report\.

   1. Select a self\-managed license type from the drop down list\. This is the type of license that the usage report will be generating data on\.

   1. Choose the report types to generate\.

   1. Choose the frequency by which License Manager will publish the reports, you can choose **Once every 24 hours**, **Once every 7 days** or **Once every 30 days**\.

   1. \(Optional\) Add **Tags** to track the usage report resource\.

1. Select **Create usage report**\.

A new usage report will begin publishing reports within 60 minutes or less\.

If you do not already have an S3 bucket associated with your account, License Manager will create a new Amazon S3 bucket in your account when you create a usage report\. If you have previously enabled **Cross\-account inventory search** reports will be sent to the S3 bucket created by License Manager when **Cross\-account inventory search** was enabled\.

Reports are stored in your bucket with the following Amazon S3 URI pattern:

```
s3://aws-license-manager-service-*/Reports/usage-report-name/year/months/day/report-id.csv
```

## Editing your usage reports<a name="view-report-generators"></a>

 You can view and make changes to your usage reports from the License Manager console at any time\. The **usage reports** table lists all the usage reports created for your account, from the table you can get an overview of your different reports, pivot to the Amazon S3 bucket associated with your usage reports, and view the status of report generation\.

**To edit a usage report**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Usage reports**\.

1. Choose the usage report you want to edit from the table, then select **View details**\.

1. Select **Edit** to make changes to the usage report\.

1. Make the desired changes to your usage report then choose **Save changes**\.

An updated usage report will generate a new report within an hour\.

**Note**  
Changing the name of your usage report will send future reports to a new folder in your License Manager S3 bucket reflecting the new name\.

## Deleting a usage report<a name="delete-report-generators"></a>

Deleting a usage report stops the generation of new reports, however, your Amazon S3 bucket and all your previous reports are not affected\.

**Note**  
You will be unable to delete a self\-managed license from your account if it has a usage report associated\. You must first delete that usage report\.

**To edit a usage report**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Usage reports**\.

1. Choose the usage report you want to edit from the table, then select **View details**\.

1. Select **Delete**\. This action permanently deletes the usage report\.