# License reporting in License Manager<a name="license-reporting"></a>

 Using AWS License Manager you can track the history of your license configurations by scheduling periodic snap shots of your license usage\. By setting up report generators License Manager will automatically upload reports of your license configurations to an S3 bucket based on your specifications\. You can set up multiple report generators to effectively track configurations of different license types in your environment\. 

**Note**  
AWS License Manager does not store your reports\. License Manager reports are published directly to your S3 bucket\. Once you delete a report generator, reports are no longer published to your S3 bucket\.

## Creating a report generator<a name="create-report-generator"></a>

 When you create a report generator you specify a license configuration type for License Manager to track, a frequency interval that defines how often to generate reports, and a report type\. All reports are generated in CSV format and published to an S3 bucket\. A report generator can produce one or more of following report types\.

**License configuration report**  
 This report type contains information on the number of consumed licenses and details about license configuration\. The tracked license configuration type is listed with details such as the license count, license rules, and the distribution of licenses across different resource types\.

**Resource report**  
This report type gives you details about your tracked resources and their license consumption\. Each tracked resource using the specified license configuration type is listed with details such as the license ID, the status of the resource, and the AWS account ID that owns the resource\.

**To create a report generator**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Reports**\. Then, from the **Create report generator** pane define the parameters for the report: 

   1. Enter a **Name** and optional **Description** for your generator\.

   1. Select a license configuration type from the drop down list\. This is the type of license that the report generator will be generating data on\.

   1. Choose the report types to generate\.

   1. Choose the frequency by which License Manager will publish the reports, you can choose **Once every day**, **Once every week** or **Once every month**\.

   1. \(Optional\) Add **Tags** to track the report generator resource\.

1. Select **Create report generator**\.

A new report generator will begin publishing reports within 60 minutes or less\.

If you do not already have an S3 bucket associated with your account, License Manager will create a new Amazon S3 bucket in your account when you create a report generator\. If you have previously enabled **Cross\-account inventory search** reports will be sent to the S3 bucket created by License Manager when **Cross\-account inventory search** was enabled\.

Reports are stored in your bucket with the following Amazon S3URI pattern:

```
s3://aws-license-manager-service-*/Reports/report-generator-name/year/months/day/report-id.csv
```

## Editing your report generators<a name="view-report-generators"></a>

 You can view and make changes to your report generators from the License Manager console at any time\. The **Report generators** table lists all the report generators created for your account, from the table you can get an overview of your different reports, pivot to the Amazon S3 bucket associated with your report generators, and view the status of report generation\.

**To edit a report generator**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Reports**\.

1. Choose the report generator you want to edit from the table, then select **View details**\.

1. Select **Edit** to make changes to the report generator\.

1. Make the desired changes to your report generator then choose **Save changes**\.

An updated report generator will generate a new report within an hour\.

**Note**  
Changing the name of your report generator will send future reports to a new folder in your License Manager S3 bucket reflecting the new name\.

## Deleting a report generator<a name="delete-report-generators"></a>

Deleting a report generator stops the generation of new reports, however, your Amazon S3 bucket and all your previous reports are not affected\.

**Note**  
You will be unable to delete a license configuration from your account if it has a report generator associated with\. You must first delete that report generator\.

**To edit a report generator**

1. Open the License Manager console at [https://console\.aws\.amazon\.com/license\-manager/](https://console.aws.amazon.com/license-manager/)\.

1. From the navigation panel choose **Reports**\.

1. Choose the report generator you want to edit from the table, then select **View details**\.

1. Select **Delete**\. This action permanently deletes the report generator\.