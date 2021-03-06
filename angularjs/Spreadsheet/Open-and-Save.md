---
title: Open and Save with Spreadsheet widget for Syncfusion Essential JS
description: How to perform Open and Save and configure its functionalities like server mapper, import URL etc.
platform: AngularJS
control: Spreadsheet
documentation: ug
---

# Open and Save

The native data format for Spreadsheet is JSON. You can load and store JSON data with Spreadsheet. In Spreadsheet we have [`saveAsJSON`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:saveasjson "saveAsJSON") and [`loadFromJSON`](https://help.syncfusion.com/api/js/ejspreadsheet#methods:loadfromjson "loadFromJSON") method which is used to save Spreadsheet as JSON and same JSON used to render Spreadsheet.

{% highlight javascript %}

function SaveAsJSON() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    window.xlData = xlObj.saveAsJSON();
}

function loadFromJSON() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    xlObj.loadFromJSON(window.xlData);
}

{% endhighlight %}


When you open an excel file, it needs to be read and converted to client side Spreadsheet model. The converted client side Spreadsheet model is sent as JSON which is used to render Spreadsheet. Similarly, when you save the Spreadsheet, the client Spreadsheet model is sent to the server as JSON for processing and saved. [`Server configuration`](https://help.syncfusion.com/angularjs/spreadsheet/open-and-save#server-configuration "Server configuration") is used for this process.

## Open 

The Spreadsheet can open excel documents as like excel application with its data, style, format. To enable open option in Spreadsheet set `e-allowimport` option as `true`. Since Spreadsheet uses a server side helper to open document, set `importmapper` in `e-importsettings` to map server action.

{% highlight html %}
<body ng-controller="SpreadsheetCtrl">
     <div id="Spreadsheet" ej-spreadsheet e-allowimport="true" e-importsettings-importmapper="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/Import"></div>
</body>

{% endhighlight %}

{% highlight javascript %}
var syncApp = angular.module("defaultApp", ["ngRoute", "ejangular"]);
    syncApp.controller('SpreadsheetCtrl', function ($scope,$rootScope) {
    });
{% endhighlight %}

Following file types can be opened in Spreadsheet

* XLS
* XLSX
* CSV

[`Click`](http://js.syncfusion.com/demos/web/#!/azure/spreadsheet/importexport "Click") here to view online demo sample.
You can open excel documents in following ways,

1. Initial settings
2. Methods
3. User Interface

### Initial settings

The Spreadsheet can load excel documents initially. The document can be specified either from client side or in server side.
To load excel documents initially from client side, set `importurl` as excel file URL in `e-importsettings`. The code snippets for document initial load on client side are as follows,

{% highlight html %}
<body ng-controller="SpreadsheetCtrl">
     <div id="Spreadsheet" ej-spreadsheet e-allowimport="true" e-importsettings-importmapper="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/Import"
     e-importsettings-importurl="http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx"></div>
</body>

 {% endhighlight %}

{% highlight javascript %}
var syncApp = angular.module("defaultApp", ["ngRoute", "ejangular"]);
    syncApp.controller('SpreadsheetCtrl', function ($scope,$rootScope) {
    });
{% endhighlight %}

To load excel documents initially from server side, set `importonload` as `true` and assign document stream or URL in the server. The code snippets for document initial load from server side are as follows,

{% highlight html %}
<body ng-controller="SpreadsheetCtrl">
     <div id="Spreadsheet" ej-spreadsheet e-allowimport="true" e-importsettings-importmapper="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/Import" e-importsettings-importonload ="true"></div>
</body>
{% endhighlight %}

{% highlight c# %}

public class JSXLExportController : ApiController
{
    [OperationContract]
    [WebGet(BodyStyle = WebMessageBodyStyle.Bare)]
    [System.Web.Http.ActionName("Import")]
    [AcceptVerbs("Post")]
    public HttpResponseMessage Import()
    {
        ImportRequest importRequest = new ImportRequest();
        importRequest.Url = "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx";           
        string str = Spreadsheet.Open(importRequest);
        return new HttpResponseMessage() { Content = new StringContent(str, Encoding.UTF8, "text/plain") };
    }
}

{% endhighlight %}

![](Open-and-Save_images/Open-and-Save_img1.png)

### Methods

To open an excel document, [`import`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:import "import") method should be called with import options as a parameter. The Spreadsheet can open excel document as a stream or file URL.

#### Stream
Spreadsheet can open excel document as a stream and the document stream was either from the client side or it can be specified in server side. The code snippets to open excel document as a stream from client side are as follows,

{% highlight javascript %}

function fileOpen(args) {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet"),
    stream = args.files[0]; // file stream from ejUploadbox
    xlObj["import"]({ file: stream });
}

{% endhighlight %}

The code snippets to specify excel document as stream in server side are as follows,

{% highlight c# %}

[OperationContract]
[WebGet(BodyStyle = WebMessageBodyStyle.Bare)]
[System.Web.Http.ActionName("Import")]
[AcceptVerbs("Post")]
public HttpResponseMessage Import()
{            
    ImportRequest importRequest = new ImportRequest();
    importRequest.FileStream = getFileStream(); // assign file stream            
    string str = Spreadsheet.Open(importRequest);
    return new HttpResponseMessage() { Content = new StringContent(str, Encoding.UTF8, "text/plain") };
}

{% endhighlight %}

#### File URL
Spreadsheet can open excel document from specified file URL. The file URL can be specified either from client side or in server side.
The code snippets to open excel document as URL from client side are as follows,

{% highlight javascript %}

function fileOpen() {
    var xlObj = $("#Spreadsheet").data("ejSpreadsheet");
    xlObj["import"]({Url: "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx"});
}

{% endhighlight %}

The code snippets to specify excel document as URL in server side are as follows,

{% highlight c# %}

[OperationContract]
[WebGet(BodyStyle = WebMessageBodyStyle.Bare)]
[System.Web.Http.ActionName("Import")]
[AcceptVerbs("Post")]
public HttpResponseMessage Import()
{
    ImportRequest importRequest = new ImportRequest();
    importRequest.Url = "http://mvc.syncfusion.com/Spreadsheet/LargeData.xlsx";
    string str = Spreadsheet.Open(importRequest);
    return new HttpResponseMessage() { Content = new StringContent(str, Encoding.UTF8, "text/plain") };
}

{% endhighlight %}

### User Interface

You can dynamically open excel document by clicking the file menu in ribbon and choose Open to upload excel file.

## Save

The Spreadsheet can save its data, style, format into an excel file. To enable save option in Spreadsheet set `allowexporting` option in `e-exportsettings` as `true`. Since Spreadsheet uses server side helper to save documents set `excelurl` in `e-exportsettings` option.

{% highlight html %}

<body ng-controller="SpreadsheetCtrl">
     <div id="Spreadsheet" ej-spreadsheet ej-spreadsheet e-exportsettings-allowexporting="true"
         e-exportsettings-excelurl="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/ExcelExport "
         e-exportsettings-pdfurl="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/PdfExport "
         e-exportsettings-csvurl="http://js.syncfusion.com/demos/ejservices/api/Spreadsheet/CsvExport "></div>
</body>
{% endhighlight %}

{% highlight javascript %}
var syncApp = angular.module("defaultApp", ["ngRoute", "ejangular"]);
    syncApp.controller('SpreadsheetCtrl', function ($scope,$rootScope) {
    });

{% endhighlight %}

You can save Spreadsheet contents with following file types

* XLS
* XLSX
* CSV
* PDF

[`Click`](http://js.syncfusion.com/demos/web/#!/azure/spreadsheet/importexport "Click") here to view online demo sample.
You can save excel documents in following ways

1. Methods
2. User Interface

### Methods

To save Spreadsheet document as excel file, [`export`](http://help.syncfusion.com/api/js/ejspreadsheet#methods:xlexport-export "export") method should be called with file type as parameter. The code snippets to save Spreadsheet document are as follows,

{% highlight javascript %}

function saveAsFile() {
    var xlObj = $("#spreadsheet").data("ejSpreadsheet");
    xlObj.XLExport["export"](ej.Spreadsheet.exportType.Excel);
}

{% endhighlight %}

### User Interface

You can dynamically save spreadsheet by clicking file menu in ribbon and choose SaveAs option.

## Server Configuration 

The import from excel and export to excel is processed in server-side only, through `Syncfusion.EJ.Export` helper functions provided for .NET Framework. So, to use importing and exporting in your projects, it is required to create a server with any of the following web services.

* WebAPI
* WCF Service
* ASP.NET MVC Controller Action

Following code snippets demonstrate open option using WebAPI controller.

{% highlight c# %}

public class JSXLExportController : ApiController
{
    [OperationContract]
    [WebGet(BodyStyle = WebMessageBodyStyle.Bare)]
    [System.Web.Http.ActionName("Import")]
    [AcceptVerbs("Post")]
    public HttpResponseMessage Import()
    {
        ImportRequest importRequest = new ImportRequest();
        importRequest.FileStream = HttpContext.Current.Request.Files[0].InputStream;            
        string str = Spreadsheet.Open(importRequest);
        return new HttpResponseMessage() { Content = new StringContent(str, Encoding.UTF8, "text/plain") };
    }

    [System.Web.Http.ActionName("ExportToExcel")]
    [AcceptVerbs("POST")]
    public void ExportToExcel()
    {
        string sheetModel = HttpContext.Current.Request.Params["sheetModel"], sheetData = HttpContext.Current.Request.Params["sheetData"];
        Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.XLSX, ExcelVersion.Excel2013);
    }

    [System.Web.Http.ActionName("ExportToCsv")]
    [AcceptVerbs("Post")]
    public void ExportToCsv()
    {
        string sheetModel = HttpContext.Current.Request.Params["sheetModel"], sheetData = HttpContext.Current.Request.Params["sheetData"];
        Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.CSV);
    }

    [System.Web.Http.ActionName("ExportToPdf")]
    [AcceptVerbs("Post")]
    public void ExportToPdf()
    {
        string sheetModel = HttpContext.Current.Request.Params["sheetModel"], sheetData = HttpContext.Current.Request.Params["sheetData"];
        Spreadsheet.Save(sheetModel, sheetData, "sample", ExportFormat.PDF);
    }
}

{% endhighlight %}

N> To export as `Stream` skip file name parameter in `Save` method. For more details refer below code snippets,<br>
   Stream stream = Spreadsheet.Save(sheetModel, sheetData, ExportFormat.XLSX, ExcelVersion.Excel2013);

### Server dependencies

Import and Export Helper functions are available in the assembly `Syncfusion.EJ.Export`, which is available in Essential Studio and Essential JavaScript builds. The full list of assemblies needed for Spreadsheet import and export are as follows.

1. Syncfusion.EJ
2. Syncfusion.EJ.Export
3. Syncfusion.Linq.Base
4. Syncfusion.Compression.Base
5. Syncfusion.DocIO.Base
6. Syncfusion.XlsIO.Base
7. Syncfusion.PDF.Base

N> 1. The above mentioned assemblies will be available in below location after Essential Studio build installation.
N> 2. C:\Program Files (x86)\Syncfusion\Essential Studio\x.x.x.x\precompiledassemblies\x.x.x.x\y.y.
N> 3. x.x.x.x defines build version of Essential Studio and y.y defines .NET Framework version.
