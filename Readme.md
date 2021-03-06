## Power BI Embedded ##

>This repository contains a sample Web App with a Power BI Embedded report.
>In order to use it with your own reports, you need to modify Web.config, and put the data from your Power BI Embedded Report in Azure. 
> You need the Access Key, the Workspace Collection Name and the Workspace Id.
```xml
 <appSettings file="Cloud.config">
    <add key="powerbi:AccessKey" value="" />
    <add key="powerbi:WorkspaceCollection" value="" />
    <add key="powerbi:WorkspaceId" value="" />
  </appSettings>
```
> If you don't know how to get this info from your dashboards, you need to make sure you first uploaded the pbix file to your PowerBI Embedded workspace. Here's a reference on how you can achieve this:

>[Upload a local PBIX file using the import API](https://powerbi.microsoft.com/fr-fr/blog/upload-a-local-pbix-file-using-the-import-api/)

> After you configure this data, you can run the application and start testing!

### The solution ###
> In order to be able to embedd the dashboards, we need to include PowerBI Package from NuGET. 
![NuGET](imgs/powerbi_1.png)

We have two classes in the Model to look at: ReportViewModel and ReportsViewModel. Both classes uses Microsoft Power BI API.
In the Controllers section, we have DashboardController. This class generates the PowerBIClient environment with the credentials we have, and gets the list of reports on our PowerBI workspace.
```csharp

public DashboardController()
        {
            this.workspaceCollection = ConfigurationManager.AppSettings["powerbi:WorkspaceCollection"];
            this.workspaceId = ConfigurationManager.AppSettings["powerbi:WorkspaceId"];
            this.accessKey = ConfigurationManager.AppSettings["powerbi:AccessKey"];
            this.apiUrl = ConfigurationManager.AppSettings["powerbi:ApiUrl"];
        }

```
