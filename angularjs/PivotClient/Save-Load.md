---
layout: post
title: Save and Load Report
description: save and load report
platform: AngularJS
control: pivotclient
documentation: ug
keywords: ejpivotclient, pivotclient, pivotclient widget, js pivotclient 
---

# Save and Load Report

Save and load report allows you to save the current report collection of PivotClient and render the control later on loading the same.

We can save and load the report in two ways.

* Database
* Local Storage

## Save Report to Database

We can store the report collection of PivotClient to database, by using the `e-saveReport` event in PivotClient.

{% highlight html %}

<div ng-controller="PivotClientCtrl">
    <div id="PivotClient1" ej-pivotclient e-saveReport="saveReportSettings" />
</div>
<script>
    angular.module('PivotClientApp', ['ejangular']).controller('PivotClientCtrl', function ($scope) {
            //..
            $scope.saveReportSettings = function(args){
                if(args.saveReportSettings)
                    return args.saveReportSetting.url = "/Olap.svc";
            };
    });
</script>

{% endhighlight %}

Service method needs to be added in WCF/WebAPI for storing PivotClient report collection in database.

For WebAPI controller, the below method needs to be added.

{% highlight c# %}

[System.Web.Http.ActionName("SaveReportToDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> SaveReportToDB(Dictionary<string, object> jsonResult)
{
    string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
    string reportName = jsonResult["reportName"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB }; //conStringforDB holds the connection adopted to the database used for storage of report collections.
    con.Open();
    SqlCeCommand cmd1 = new SqlCeCommand("insert into ReportsTable Values(@ReportName,@Reports)", con);
    cmd1.Parameters.Add("@ReportName", reportName);
    cmd1.Parameters.Add("@Reports", Encoding.UTF8.GetBytes(jsonResult["clientReports"].ToString()).ToArray());
    cmd1.ExecuteNonQuery();
    con.Close();
    return null;
}

{% endhighlight %}

For WCF controller, the below method needs to be added.

{% highlight c# %}

public Dictionary<string, object> SaveReportToDB(string reportName, string operationalMode, string analysisMode, string olapReport, string clientReports)
{
    reportName = reportName + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };//conStringforDB holds the connection adopted to the database used for storage of report collections.
    con.Open();
    SqlCeCommand cmd1 = new SqlCeCommand("insert into ReportsTable Values(@ReportName,@Reports)", con);
    cmd1.Parameters.Add("@ReportName", reportName);
    cmd1.Parameters.Add("@Reports", Encoding.UTF8.GetBytes(clientReports).ToArray());
    cmd1.ExecuteNonQuery();
    con.Close();
    return null;
}

{% endhighlight %}

## Save Report to Local Storage

We can store the report collection of PivotClient to local storage, by setting the `e-enableLocalStorage` property to true and by defining the `e-saveReport` event of PivotClient.

{% highlight html %}

<div ng-controller="PivotClientCtrl">
    <div id="PivotClient1" ej-pivotclient e-enableLocalStorage="true" e-saveReport="saveReportSettings" />
</div>
<script>
    angular.module('PivotClientApp', ['ejangular']).controller('PivotClientCtrl', function ($scope) {
            //..
            $scope.saveReportSettings = function(args){
                    var reportCollection = [];
                    if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
                        reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
                    }
                    if(args.saveReportSettings) {
                        reportCollection.push(({ reportName: args.saveReportSetting.reportName, reportCol: args.saveReportSetting.reportCollection }));
                        localStorage.pivotClientRPTCollection = JSON.stringify(reportCollection);
                    }
            };
    });
</script>

{% endhighlight %}

## Load Report from Database

We can load the stored report collection of PivotClient from database, by using the `e-fetchReport` and `e-loadReport` events in PivotClient.

{% highlight html %}

<div ng-controller="PivotClientCtrl">
    <div id="PivotClient1" ej-pivotclient e-loadReport="reportSettings" e-fetchReport="reportSettings" />
</div>
<script>
    angular.module('PivotClientApp', ['ejangular']).controller('PivotClientCtrl', function ($scope) {
            //..
            $scope.reportSettings = function(args){
                    if (args.fetchReportSetting)
                        return args.fetchReportSetting.url = "../wcf/OlapClientService.svc";
                    else if (args.loadReportSetting)
                        return args.loadReportSetting.url = "../wcf/OlapClientService.svc";
            };
    });
</script>

{% endhighlight %}

Service methods need to be added in WCF/WebAPI for storing PivotClient report collection in database.

For WebAPI controller, the below methods need to be added.

{% highlight c# %}

[System.Web.Http.ActionName("FetchReportListFromDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> FetchReportListFromDB(Dictionary<string, object> jsonResult)
{
    string reportNames = string.Empty, currentRptName = string.Empty, operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
    foreach (System.Data.DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string);
        if (currentRptName.IndexOf("##" + operationalMode + "#>>#" + analysisMode) >= 0)
        {
            currentRptName = currentRptName.Replace("##" + operationalMode + "#>>#" + analysisMode, "");
            reportNames = reportNames == "" ? currentRptName : reportNames + "__" + currentRptName;
        }
    }
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("ReportNameList", reportNames);
    return dictionary;
}

[System.Web.Http.ActionName("LoadReportFromDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> LoadReportFromDB(Dictionary<string, object> jsonResult)
{
    PivotReport report = new PivotReport();
    string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    string currentRptName = string.Empty;
    foreach (DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string).Replace("##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower(), "");
        if (currentRptName.Equals(jsonResult["reportName"].ToString()))
        {
            byte[] reportString = new byte[2 * 1024];
            reportString = (row.ItemArray[1] as byte[]);
            if (analysisMode.ToLower() == "pivot" && operationalMode.ToLower() == "servermode")
                dictionary = pivotClient.GetJsonData("LoadReport", ProductSales.GetSalesData(), Encoding.UTF8.GetString(reportString));
            else
                dictionary.Add("report", Encoding.UTF8.GetString(reportString));
            break;
        }
    }
    return dictionary;
}
private DataTable GetDataTable()
{
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    DataSet dSet = new DataSet();
    new SqlCeDataAdapter("Select * from ReportsTable", con).Fill(dSet);
    con.Close();
    return dSet.Tables[0];
}

{% endhighlight %}

For WCF controller, the below methods need to be added.

{% highlight c# %}

public Dictionary<string, object> FetchReportListFromDB(string operationalMode, string analysisMode)
{
    string reportNames = string.Empty;
    string currentRptName = string.Empty;
    foreach (System.Data.DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string);
        if (currentRptName.IndexOf("##" + operationalMode + "#>>#" + analysisMode) >= 0)
        {
            currentRptName = currentRptName.Replace("##" + operationalMode + "#>>#" + analysisMode, "");
            reportNames = reportNames == "" ? currentRptName : reportNames + "__" + currentRptName;
        }
    }
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("ReportNameList", reportNames);
    return dictionary;
}

public Dictionary<string, object> LoadReportFromDB(string reportName, string operationalMode, string analysisMode, string olapReport, string clientReports)
{
    PivotReport report = new PivotReport();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    string currentRptName = string.Empty;
    foreach (DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string).Replace("##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower(), "");
        if (currentRptName.Equals(reportName))
        {
            if (operationalMode.ToLower() == "servermode" && analysisMode == "olap")
            {
                var reportString = "";
                OlapDataManager DataManager = new OlapDataManager();
                reportString = OLAPUTILS.Utils.CompressData(row.ItemArray[1] as byte[]);
                DataManager.Reports = pivotClient.DeserializedReports(reportString);
                DataManager.SetCurrentReport(DataManager.Reports[0]);
                return pivotClient.GetJsonData("toolbarOperation", DataManager, "Load Report", reportName);
            }
            else
            {
                byte[] reportString = new byte[2 * 1024];
                reportString = (row.ItemArray[1] as byte[]);
                if (analysisMode.ToLower() == "pivot" && operationalMode.ToLower() == "servermode")
                    dictionary = pivotClient.GetJsonData("LoadReport", ProductSales.GetSalesData(), Encoding.UTF8.GetString(reportString));
                else
                    dictionary.Add("report", Encoding.UTF8.GetString(reportString));
                break;
            }

        }
    }
    return dictionary;
}

private DataTable GetDataTable()
{
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    DataSet dSet = new DataSet();
    new SqlCeDataAdapter("Select * from ReportsTable", con).Fill(dSet);
    con.Close();
    return dSet.Tables[0];
}

{% endhighlight %}

## Load Report from Local Storage

We can load the stored report collection of PivotClient from local storage, by setting the `e-enableLocalStorage` property to true and using the `e-LoadReport` and `e-FetchReport` events in PivotClient.

{% highlight html %}

<div ng-controller="PivotClientCtrl">
    <div id="PivotClient1" ej-pivotclient e-enableLocalStorage="true" e-loadReport="reportSettings" e-fetchReport="reportSettings" />
</div>
<script>
    angular.module('PivotClientApp', ['ejangular']).controller('PivotClientCtrl', function ($scope) {
            //..
            $scope.reportSettings = function(args){
                    var reportCollection = [];
                    if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
                        reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
                    }
                    if (args.fetchReportSetting) 
                        args.fetchReportSetting.reportList = $.map(reportCollection, function (item, index) { return item.reportName; }).join("__");
                    else if (args.loadReportSetting) 
                        args.loadReportSetting.reportCollection = $.map(reportCollection, function (item, index) { if (item.reportName == args.loadReportSetting.selectedReport) return item.reportCol; });
            };
    });
</script>

{% endhighlight %}