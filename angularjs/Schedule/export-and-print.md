---
title: Export and print the Schedule with its appointments	
description: Export/Print the complete Scheduler or specific appointment alone
platform: AngularJS
control: schedule
documentation: ug
keywords: export, import and print 
---
# Export and Print

## Export Appointments to ICS file

The Appointments can be exported as a whole collection or else a single appointment alone can be exported from the Scheduler. By default, the appointments are exported to .ics format which can then be imported and used in any of the other external calendars.

### Single Appointment Exporting

A single appointment can be exported by making use of its Id. You can achieve this functionality by making use of an **exportSchedule** method by passing the id of an appointment to export as one of its parameter. 

It can also be achieved in another way by enabling the context menu settings and then adding a custom menu option for export appointment functionality. When right clicked on an appointment, and **export Appointment** option is chosen, the exporting functionality can be handled through the `e-menuitemclick` event, within which the **exportSchedule** method should be defined with the following parameters,

* Action name (to be called in the server-side)
* Server Event (optional)
* Appointment Id (mandatory for single Appointment exporting)

The following code example shows the way to export single appointment from the Scheduler.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataManager" e-contextmenusettings-enable="true" e-menuitemclick="onMenuItemClick">
            <e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="open" e-text="Open Appointment"></e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="delete" e-text="Delete Appointment"></e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="export" e-text="Export Appointment"></e-contextmenusettings-menuitems-appointment>
            </e-contextmenusettings-menuitems-appointment>
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataManager = ej.DataManager({
            url: "Home/GetData",
            adaptor: new ej.UrlAdaptor()
        });
        $scope.setDate = new Date(2017, 1, 7);
    });
    // This function executes, when any of the menu options are clicked in the context menu
    $scope.onMenuItemClick = function(args) {
        if (args.events.ID == "export") {
            var obj = angular.element("#Schedule1").data("ejSchedule");
            // exportSchedule() method will send a post to the server-side to call a specified action.
            obj.exportSchedule("Home/ExportToICS", null, args.targetInfo.Id);
        }
    }
    </script>
</body>
</html>

{% endhighlight %}

N> The Id value of the appointment passed in the above code example can be retrieved in the server-side action through Request.Form["AppointmentId"], as the id passed from the script is stored as hidden value in the input field of the form under this name internally.

### Exporting all Appointments

To export the entire Scheduler appointments, the same **exportSchedule** method can be used without passing the id value to its parameter list. To achieve this, keep an individual button to export, and when it is clicked - the Scheduler can be allowed to export all the appointments.

The following code example depicts the way to export all the Scheduler appointments as a whole.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <!-- Button div for Export Option-->
        <button id="Btn" ej-button e-width="70px" e-height="30px" e-click="onClick">Export</button>
        <!--Container for ejScheduler widget-->
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataManager">
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataManager = ej.DataManager({
            url: "Home/GetData",
            adaptor: new ej.UrlAdaptor()
        });
        $scope.setDate = new Date(2017, 1, 7);
    });
    // Clicking on the export button will call this method
    $scope.onClick = function(args) {
        var obj = angular.element("#Schedule1").data("ejSchedule");
        // Calls the server-side action ExportToICS
        obj.exportSchedule("Home/ExportToICS", null, null);
    }
    </script>
</body>
</html

{% endhighlight %}

The server-side action **ExportToICS** contains the following code example to export the Scheduler appointments.

{% highlight c# %}

public void ExportToICS(FormCollection form)
{
	IEnumerable data;
	string JSONModel = Request.Form["ScheduleModel"];
	var model = JsonConvert.DeserializeObject<Dictionary<string, object>>(JSONModel);
	var Id = Request.Form["AppointmentId"];
	if(Id != null)
		// To export single appointment
		data = db.DefaultSchedules.Where(app => app.Id.ToString() == Id.ToString()).ToList();
	else
		// To export all the appointments
		data = db.DefaultSchedules.ToList();
	ScheduleExport obj = new ScheduleExport(model, data);
}

{% endhighlight %}

## PDF Export

Scheduler supports exporting it along with all its appointments in PDF format, for which the same **exportSchedule** method can be used without passing any id value to its parameter list. To achieve this, keep an individual button to export and when it is clicked, the Scheduler with appointments can be allowed to export as PDF.

The following code example depicts the way to export the Scheduler with appointments in PDF format.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
         <!-- Button div for Export Option-->
        <button id="btnExport" ej-button e-width="70px" e-height="30px" e-click="onExportClick">Export</button>
        <!--Container for ejScheduler widget-->
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataManager">
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataManager = ej.DataManager({
            url: "Home/GetData",
            adaptor: new ej.UrlAdaptor()
        });
        $scope.setDate = new Date(2017, 1, 7);
    });
    // Clicking on the export button will call this method
    $scope.onExportClick=function(e) {
        var obj = angular.element("#Schedule1").data("ejSchedule");
        // Calls the server-side action PDFExport
        obj.exportSchedule("Home/PDFExport", null, null);
    }
    </script>
</body>
</html

{% endhighlight %}

The server-side action **PDFExport** contains the following code example to export the Scheduler.

{% highlight c# %}

public ActionResult PDFExport(string scheduleModel)
{
    PdfExport exp = new PdfExport();
    JavaScriptSerializer serializer = new JavaScriptSerializer();
    SchedulePDFExport convert= new SchedulePDFExport();
    // Here calling the public method to convert the model values to ScheduleProperties type from string type
    ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(scheduleModel); 
    // Here converting the schedule appointments data into enumerable object by deserializing              
    IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable));
    // Here passing the theme values from enum collection
    PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron,Request.Form["locale"]);
    document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
    return RedirectToAction("PDFExportController");
}

{% endhighlight %}

N> To pass the theme value as a string instead of the enum value, refer to the following code example of passing the string type theme value.
{% highlight c# %}
    PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, "flat-saffron",Request.Form["locale"]);
{% endhighlight %}

### Setting Page Options:

It is possible to set/change the PDF page settings such as size, margins (left, right, top and bottom), transition, and rotate angle and header/footer values by passing the page settings and page document template object values into the export method. 

#### Page Settings:
You can set/apply the following page property values to the PDF file before exporting it with the Scheduler by using the `PdfPageSettings` object. 
a)	Page Size
b)	Orientation
c)	Margins ( Left, Right, Top, Bottom)
d)	Transition ( Direction, Dimension, Duration, Motion, PageDuration, Scale, Style)
e)	Rotate ( RotateAngle0, RotateAngle90, RotateAngle180, RotateAngle270)
f)	Height
g)	Width

To apply the above page setting values, you need to create an object for the `PdfPageSettings` class. Then, you can assign the values to the available properties within it such as Size = PdfPageSize.A3, Orientation = PdfPageOrientation.Landscape and so on. Once done, pass this object into the export method which will set these page settings values to the PDF file before exporting it. Refer to the following code example (server-side) to set/change the page settings values.

{% highlight c# %}
    public ActionResult PDFExport(string scheduleModel)
        {
            JavaScriptSerializer serializer = new JavaScriptSerializer();
            SchedulePDFExport convert= new SchedulePDFExport();
            ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(scheduleModel); // Here calling the public method to convert the model values to ScheduleProperties type from string type
            IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable)); // Here deserialize the appointments to enumerable object
            PdfExport exp = new PdfExport();

            // Here the 50f is the default value for the margins. If you are not assigning any separate values like Margins.Left = 15 means 50f value will be setting to all the Margin properties.
            PdfPageSettings pageSettings = new PdfPageSettings(50f);  

            // Here you can assign the PdfPageSize enum value (ex: A3, A4)
            pageSettings.Size = PdfPageSize.A3;  

            // Here Landscape value assigned to the orientation. You can set either Landscape/Portrait for this Orientation property
            pageSettings.Orientation = PdfPageOrientation.Landscape; 

            // Here assigned different values for the margins 
            pageSettings.Margins.Left = 15;
            pageSettings.Margins.Right = 15;
            pageSettings.Margins.Top = 20;
            pageSettings.Margins.Bottom = 20;

            // Here assigned the Transition Direction as BottomToTop. You can also set any of the Transition values to this property
            pageSettings.Transition.Direction= PdfTransitionDirection.BottomToTop;

            // Here assigned the Rotate Angle as RotateAngle180. You can also set any of the Rotate values to this property
            pageSettings.Rotate = PdfPageRotateAngle.RotateAngle180;

            // Here passing the page settings object value into the export method.
            PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], pageSettings);
            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
            return RedirectToAction("PDFExportController");
        }
{% endhighlight %}

#### Header/Footer Settings:

You can also set the header and footer options to the PDF page before it is being exported, by passing the `PDFDocumentTemplate` object values as mentioned in the following code example. 

{% highlight c# %}
    public ActionResult PDFExport(string scheduleModel)
        {
            JavaScriptSerializer serializer = new JavaScriptSerializer();
            SchedulePDFExport convert= new SchedulePDFExport();
            ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(scheduleModel); // Here calling the public method to convert the model values to ScheduleProperties type from string type

            IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable)); // Here deserialize the appointments to enumerable object
            PdfExport exp = new PdfExport();
            PdfDocument document = new PdfDocument();
            PdfPage pdfPage = document.Pages.Add();

            //Create a header and draw the string.
            // Here the bounds value is used to store the position/axis value, where the header and footer content to be displayed
            RectangleF bounds = new RectangleF(0, 0, document.Pages[0].GetClientSize().Width, 50);

            // Creating object for the PdfPageTemplateElement
            PdfPageTemplateElement header = new PdfPageTemplateElement(bounds);

            // Here setting the font style and color to display the header/footer content
            PdfSolidBrush brush = new PdfSolidBrush(Color.Gray);
            PdfFont font = new PdfStandardFont(PdfFontFamily.Helvetica, 6, PdfFontStyle.Bold);
            PdfStringFormat format = new PdfStringFormat();
            format.Alignment = PdfTextAlignment.Center;
            format.LineAlignment = PdfVerticalAlignment.Middle;
            header.Graphics.DrawString("Schedule", font, brush, new RectangleF(0, 18, header.Width, header.Height), format);

            //Create a Page template that can be used as footer (here creating template to display the page number).
            PdfPageTemplateElement footer = new PdfPageTemplateElement(bounds);

            //Create page number field.
            PdfPageNumberField pageNumber = new PdfPageNumberField(font, brush);

            //Create page count field.
            PdfPageCountField count = new PdfPageCountField(font, brush);

            //Add the fields in composite fields.
            PdfCompositeField compositeField = new PdfCompositeField(font, brush, "Page {0} of {1}", pageNumber, count);
            compositeField.Bounds = footer.Bounds;

            //Draw the composite field in footer.
            compositeField.Draw(footer.Graphics, new PointF(470, 40));
            PdfDocumentTemplate headerFooterTemplate = new PdfDocumentTemplate();
            
            //Here assigning the header template value to the PdfDocumentTemplate Object.
            headerFooterTemplate.Top = header; 

            //Here assigning the footer template value to the PdfDocumentTemplate Object.
            headerFooterTemplate.Bottom = footer;

            //Here passing the PdfDocumentTemplate Object value into the export method.
            document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], headerFooterTemplate);
            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
            return RedirectToAction("PDFExportController");
        }

{% endhighlight %}

N>The header and footer values can be passed to the PDF file only through the template option. In the above mentioned code example, the template has been written with the text “Schedule” to display it as the header text and the page number (ex: Page 1 of 2) has been displayed in the footer part. 

It is also possible to pass both the `PageSettings` and header/footer template objects in the export method altogether to apply the page settings as well as the header and footer options to the PDF file which can be referred from the following code example,

{% highlight c# %}
        public ActionResult PDFExport(string scheduleModel)
        {
            //Here add the code example of both the page settings and header/footer values settings.
            
            //Then pass both PdfPageSettings and PdfDocumentTemplate object into the export method.            
            
            document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], pageSettings, headerFooterTemplate);
            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
            return RedirectToAction("PDFExportController");
        }

{% endhighlight %}


## Print

Two types of Print options are available – either to print the entire Scheduler layout including all the appointments in it or else to print any particular appointment alone. The public method **print** is used to print the entire Scheduler.

### Print the Scheduler

The following code example shows the way to print the entire Scheduler, by keeping an extra button in a page – on which clicking the button will print the entire Scheduler.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <!-- Button div for Print Option-->
        <button id="Btn" ej-button e-width="70px" e-height="30px" e-click="onClick">Print</button>
        <!--Container for ejScheduler widget-->
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataSource">
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataSource = [{
            Id: 1,
            Subject: "Wild Discovery",
            StartTime: new Date(2017, 1, 7, 9, 00),
            EndTime: new Date(2017, 1, 7, 10, 30)
        }];
        $scope.setDate = new Date(2017, 1, 7);
    });
    // Clicking on the print button will call this method
    $scope.onClick = function(args) {
        var obj = angular.element("#Schedule1").data("ejSchedule");
        obj.print();
    }
    </script>
</body>
</html>

{% endhighlight %}

### Printing Specific Appointments

To print a particular appointment, either the default context menu **print** option can be used or else the **print** method can be used by passing the id of the appointment to be printed as its argument. 

#### Using Context Menu

Here, the print action is handled internally by default, so that when an appointment is right clicked – choosing print option from the context menu that pops-out will automatically print that particular appointment.

N> To handle this functionality, the context menu settings needs to be enabled with print option added to the appointment items.

The following code example depicts the way to print a particular appointment.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataSource" e-contextmenusettings-enable="true">
            <e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="open" e-text="Open Appointment"></e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="delete" e-text="Delete Appointment"></e-contextmenusettings-menuitems-appointment>
                <e-contextmenusettings-menuitems-appointment e-id="print" e-text="Print Appointment"></e-contextmenusettings-menuitems-appointment>
            </e-contextmenusettings-menuitems-appointment>
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataSource = [{
            Id: 1,
            Subject: "Wild Discovery",
            StartTime: new Date(2017, 1, 7, 9, 00),
            EndTime: new Date(2017, 1, 7, 10, 30)
        }];
        $scope.setDate = new Date(2017, 1, 7);
    });
    </script>
</body>
</html>

{% endhighlight %}

#### Using print() method

The public method `print` needs to be used here by passing the appointment object as its argument, that needs to be printed.

For example, here the below code example depicts the way to print the particular appointment programmatically by calling the **print** function within the `e-appointmentclick` event, which triggers whenever the user clicks on an appointment.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="dataSource" e-appointmentclick="onAppointmentClick">
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
        $scope.dataSource = [{
            Id: 1,
            Subject: "Wild Discovery",
            StartTime: new Date(2017, 1, 7, 9, 00),
            EndTime: new Date(2017, 1, 7, 10, 30)
        }];
        $scope.setDate = new Date(2017, 1, 7);
    });
    $scope.onAppointmentClick = function(args) {
        var schObj = angular.element("#Schedule1").data("ejSchedule");
        schObj.print(args.appointment);
    }
    </script>
</body>
</html>

{% endhighlight %}

## Import Appointments

To import appointments into the Scheduler, server-side method `renderingImportAppointments` needs to be used, which returns the list of appointments retrieved from the specified file path.

Refer the following code example to import the appointments into Scheduler.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <!--Button div for Import Option-->
        <button id="Btn" ej-button e-width="70px" e-height="30px" e-click="ScheduleImport">Import</button>
        <!--Container for ejScheduler widget-->
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px">
        </ej-schedule>
    </div>
    <script type="text/javascript">
    angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {       
    });
    $scope.ScheduleImport = function() {
    function ScheduleImport() {
        var dataManger = ej.DataManager({ url: '@Url.Action("ScheduleImportData", "Home")', crossDomain: true });
        angular.element("#Schedule1").ejSchedule({
            appointmentSettings: {
                dataSource: dataManger
            }
        });
    }
    </script>
</body>
</html>

{% endhighlight %}

The server-side action `ScheduleImportData` contains the following code example to import the Scheduler appointments.

{% highlight c# %}

public JsonResult ScheduleImportData() {
    var destinationPath = @"Filepath\iCalender.ics";
    ScheduleImport importApps = new ScheduleImport();
    var app = importApps.renderingImportAppointments(destinationPath);
    int intMax = app.Max(a => a.Id);
    List<ScheduleAppointmentsObjData> result = new List<ScheduleAppointmentsObjData>();
    for (var i = 0; i < app.Count; i++) {
        app[i].Id = intMax + 1;
        ScheduleAppointmentsObjData row = new ScheduleAppointmentsObjData(app[i].Id, app[i].Subject, app[i].Location, app[i].StartTime, app[i].EndTime, app[i].Description, null, null, app[i].Recurrence, null, null, app[i].AppointmentCategorize, null, app[i].AllDay, null, null, app[i].RecurrenceRules, null, null);
        result.Add(row);
        intMax = app[i].Id;
    }
    return Json(result, JsonRequestBehavior.AllowGet);
}

{% endhighlight %}
