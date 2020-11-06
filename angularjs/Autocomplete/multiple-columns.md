---
layout: post
title: multiple-columns
description: multiple columns
platform: AngularJS
control: Autocomplete
documentation: ug
---

## Multiple Columns

The Autocomplete allows list of data to be displayed in several columns and column collection can be defined and customized through the [e-multicolumnsettings ](http://help.syncfusion.com/api/js/ejautocomplete)property.

In AutoComplete Multiple Column search is based on [searchColumnIndices](https://help.syncfusion.com/api/js/ejautocomplete#members:multicolumnsettings-searchColumnIndices) property which allows user to search text for any number of fields in the suggestion list without modifying the selected text format.

In AutoComplete Multiple Column searched value is updated to autocomplete input box based on [stringFormat](https://help.syncfusion.com/api/js/ejautocomplete#members:multiColumnSettings-stringFormat) property which specifies column indices values to  updated.

NOTE :NOTE: 1. [stringFormat ](http://help.syncfusion.com/api/js/ejautocomplete)as “{0} ({1})” means search based on 0, 1 and 2 columns data.
            2. If [searchColumnIndices](https://help.syncfusion.com/api/js/ejautocomplete#members:multicolumnsettings-searchColumnIndices) given as [0,1,2], then the column search will done using 0,1,2 column data alone.

<table>
<tr>
<td>
Name</td><td>
Description</td></tr>
<tr>
<td>
multiColumnSettings.enable</td><td>
Allow list of data to be displayed in several columns.</td></tr>
<tr>
<td>
multiColumnSettings.showHeader</td><td>
Allow header text to be displayed in corresponding columns.</td></tr>
<tr>
<td>
multiColumnSettings.stringFormat</td><td>
Displayed selected value and autocomplete search is based on mentioned column value specified in that format.</td></tr>
<tr>
<td>
multiColumnSettings.columns</td><td>
Field and Header Text collections can be defined and customized through this field.</td></tr>
<tr>
<td>
multiColumnSettings.columns.field</td><td>
Get or set a value that indicates to display the columns in the autocomplete mapping with column name of the dataSource.</td></tr>
<tr>
<td>
multiColumnSettings.columns.headerText</td><td>
Get or set a value that indicates to display the title of that particular column.</td></tr>
<tr>
<td>
multiColumnSettings.columns.cssClass</td><td>
Used to set the user defined cssClass for the particular column</td></tr>
<tr>
<td>
multiColumnSettings.columns.type</td><td>
Used to define the data type for a particular column </td></tr>
<tr>
<td>
multiColumnSettings.columns.filterType</td><td>
Used to set the search filter type for the column</td></tr>
<tr>
<td>
multiColumnSettings.columns.headerTextAlign</td><td>
Used to align or position the header value in the column</td></tr>
<tr>
<td>
multiColumnSettings.columns.textAlign</td><td>
Used to align or position all the values in a column</td></tr>
</table>




{% highlight html %}



                <input id="autoCompleteBox" type="text" ej-autocomplete e-width="50%" e-datasource="multicolumndataList" e-showpopupbutton="true"  e-fields-key="multicolumnkey" e-fields-text="multicolumntext" e-multicolumnsettings="multicolumncolset"  />


<script type="text/javascript">
    angular.module('syncApp', ['ejangular'])
             .controller('AutoCompleteCtrl', function ($scope) {  
       $scope.multicolumndataList = [{ "EmployeeID": 1, "FirstName": "Nancy", "City": "Seattle" },
            { "EmployeeID": 2, "FirstName": "Andrew", "City": "Tacoma" },
            { "EmployeeID": 3, "FirstName": "Janet", "City": "Kirkland" },
            { "EmployeeID": 4, "FirstName": "Margaret", "City": "Redmond" },
            { "EmployeeID": 5, "FirstName": "Steven", "City": "London" },
            { "EmployeeID": 6, "FirstName": "Michael", "City": "London" },
            { "EmployeeID": 7, "FirstName": "Robert", "City": "London" },
            { "EmployeeID": 8, "FirstName": "Laura", "City": "Seattle" },
            { "EmployeeID": 9, "FirstName": "Anne", "City": "London" },
            { "EmployeeID": 10, "FirstName": "Laura", "City": "Seattle" },
            { "EmployeeID": 11, "FirstName": "Janet", "City": "Kirkland" },
            { "EmployeeID": 12, "FirstName": "Michael", "City": "London" },
            { "EmployeeID": 13, "FirstName": "Steven", "City": "London" },
            { "EmployeeID": 14, "FirstName": "Andrew", "City": "Tacoma" },
            { "EmployeeID": 15, "FirstName": "Robert", "City": "London" },
            { "EmployeeID": 16, "FirstName": "Margaret", "City": "Redmond" },
            { "EmployeeID": 17, "FirstName": "Steven", "City": "London" },
            { "EmployeeID": 18, "FirstName": "Michael", "City": "London" },
            { "EmployeeID": 19, "FirstName": "Robert", "City": "London" },
            { "EmployeeID": 20, "FirstName": "Laura", "City": "Seattle" },
            { "EmployeeID": 21, "FirstName": "Anne", "City": "London" },
            { "EmployeeID": 22, "FirstName": "Margaret", "City": "London" },
            { "EmployeeID": 23, "FirstName": "Andrew", "City": "Tacoma" },
            { "EmployeeID": 24, "FirstName": "Janet", "City": "Kirkland" },
            { "EmployeeID": 25, "FirstName": "Margaret", "City": "Redmond" },
            { "EmployeeID": 26, "FirstName": "Steven", "City": "London" },
            { "EmployeeID": 27, "FirstName": "Michael", "City": "London" },
            { "EmployeeID": 28, "FirstName": "Robert", "City": "London" },
            { "EmployeeID": 29, "FirstName": "Laura", "City": "Seattle" },
            { "EmployeeID": 30, "FirstName": "Anne", "City": "London" },
            { "EmployeeID": 31, "FirstName": "Margaret", "City": "Redmond" },
            { "EmployeeID": 32, "FirstName": "Steven", "City": "London" }];
$scope.multicolumnkey="EmployeeID";
$scope.multicolumntext="City";
$scope.multicolumncolset = {
        stringFormat: "{0}  ({1})",
        searchColumnIndices:[0,1,2],
enable:true,
showHeader: true,
columns: [
{
                    field: "FirstName",
                    headerText: "FirstName"
                },
                {
                    field: "EmployeeID",
                    headerText: "EmployeeID"
                },
                {
                    field: "City",
                    headerText: "City"
                }
]}
});



{% endhighlight %}



Run the above code to render the following output. 

![](multiple-columns_images\multiple-columns_img1.png)



