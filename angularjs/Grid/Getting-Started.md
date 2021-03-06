---
layout: post
title: Getting Started | Grid | AngularJS | Syncfusion
description: This section describes how to create the Grid, data bind, enable paging, grouping, filtering and add summaries.
platform: AngularJS
control: Grid
documentation: ug
---
# Getting Started

Before getting started with the Grid, please refer to [this page] (http://help.syncfusion.com/js/angularjs) for general information regarding the integrating Syncfusion widget's.

## Preparing HTML document

The Grid control has the following list of external JavaScript dependencies:

* [jQuery](http://jquery.com/) 1.7.1 and later versions

* [jsRender](https://github.com/borismoore/jsrender) - to render the templates

To get started, you can use the `ej.web.all.min.js` file that encapsulates all the `ej` controls and frameworks in single file. Also use the `ej.widget.angular.min.js` script file that encapsulates the angular directives for the controls. So the complete boilerplate code is:     

{% highlight html %}

<!DOCTYPE html>
<html>
<head>
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta name="description" content="Essential Studio for JavaScript">
		<meta name="author" content="Syncfusion">
	      <title></title>
             <!-- Essential Studio for JavaScript  theme reference -->
	    <link rel="stylesheet" href="http://cdn.syncfusion.com/13.4.0.53/js/web/flat-azure/ej.web.all.min.css" />
		    <!-- Essential Studio for JavaScript  script references -->
	    <script src="https://code.jquery.com/jquery-1.10.2.min.js"></script>
		<script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
		<script src="http://cdn.syncfusion.com/13.4.0.53/js/web/ej.web.all.min.js"> </script>
		<script src="http://cdn.syncfusion.com/13.4.0.53/js/web/ej.widget.angular.min.js"> </script>
			<!-- Add your custom scripts here -->
</head>
<body>
</body>
</html>

{% endhighlight %}

N> In production, using the [custom script generator](http://helpjs.syncfusion.com/js/include-only-the-needed-widgets) is highly recommended to create custom script file with the required controls and its dependencies only. Also to reduce the file size further, please use [GZip compression](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer?hl=en) in your server.

For themes, you can use the `ej.web.all.min.css` CDN link from the given code example. To add the themes in your application, please refer to [this link](http://help.syncfusion.com/js/theming-in-essential-javascript-components).

## Create a Grid

All the Essential JavaScript directives have been encapsulated into a single module called `ejangular`, so the first step will declare dependency for this module within your AngularJS application. 

The grid can be created using `ej-grid` angular directive and its properties can be defined using the `e-` prefix followed by the property name. 

The code example for defining controls in AngularJS is as follows.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
   <body ng-controller="GridCreationCtrl">
   <div id="Grid" ej-grid e-datasource="shipdetails" >
   </div>
   <script>
      angular.module('listCtrl', ['ejangular'])
        .controller('GridCreationCtrl', function ($scope) {
            $scope.shipdetails = [
                         { Name: 'Hanari Carnes', City: 'Brazil' },
                         { Name: 'Split Rail Beer & Ale', City: 'USA' },
                         { Name: 'Ricardo Adocicados', City: 'Brazil' }
            ];
        });
   </script>
 </body>
</html>

{% endhighlight %}

![Angular Grid control](Getting-started_images/Getting-started_img1.png)
{:.image }

In previous code sample, `ej-grid` denotes the control directive for the Syncfusion's Grid angular widget and all its properties are prefixed with the letter `e-` (For example, e-datasource).

## Data Binding

The [`Data binding`](http://helpjs.syncfusion.com/js/grid/data-binding) in the grid is achieved by assigning an array of JavaScript objects to the [`dataSource`](http://help.syncfusion.com/js/api/ejgrid#members:columns-datasource) property. Refer to the following code example.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="DataBindingCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true">
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
            .controller('DataBindingCtrl', function ($scope) {
                 //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
                $scope.data = window.gridData;
                $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
            });
    </script>
</body>
</html>

{% endhighlight %}

![Data binding support of angular grid](Getting-started_images/Getting-started_img2.png)
{:.image }


## Enable Paging

`Paging` can be enabled by setting the `e-allowpaging` to `true`. This adds the pager in the bottom of the grid and page size can be customized by using the `e-pagesettings-pagesize` attribute.


{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="PagingCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true" e-pagesettings="pageset">
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
            .controller('PagingCtrl', function ($scope) {
                //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
                $scope.data = window.gridData;
                $scope.pageset = { pageSize: 8 };
                $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
            });
    </script>
</body>
</html>

{% endhighlight %}

N> _1.Pager settings can be customized by using the `e-pagesettings-pagesize` property. When it is not given the default values of `pageSize` and `pageCount` are 12 and 8 respectively.

2. The array properties of the Syncfusion widget's in angularjs has to be defined by using the scope variable.

![Page number displayed on angular grid](Getting-started_images/Getting-started_img3.png)
{:.image }



## Enable Filtering

`Filtering` can be enabled by setting the `e-allowfiltering` to `true`. By default, the filter bar row is displayed to perform filtering, you can change the filter type by using the `e-filtersettings-filterType` attribute.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="FilteringCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true" e-pagesettings-pagesize="8" e-allowfiltering="true" }>
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
            .controller('FilteringCtrl', function ($scope) {
                //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
                $scope.data = window.gridData;
                $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
            });
    </script>
</body>
</html>

{% endhighlight %}

![Filtering option of angular grid](Getting-started_images/Getting-started_img4.png)
{:.image }

## Enable Grouping

`Grouping` can be enabled by setting the `e-allowgrouping` to `true`. Columns can be grouped dynamically by drag and drop the grid column header to the group drop area. The initial grouping can be done by adding required column names in the `e-groupsettings-groupedcolumns` attribute. 

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="GroupingCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true" e-pagesettings-pagesize="8" e-allowgrouping="true" }>
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
            .controller('GroupingCtrl', function ($scope) {
                //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
                $scope.data = window.gridData;
                $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
            });
    </script>
</body>
</html>
{% endhighlight %}

![Grouping option enabled in angular grid](Getting-started_images/Getting-started_img5.png)
{:.image }

Refer to the following code example for initial grouping.


{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="GroupingCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true" e-pagesettings-pagesize="8" e-allowgrouping="true" e-groupsettings="grouping">
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
            .controller('GroupingCtrl', function ($scope) {
                //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
                $scope.data = window.gridData;
                $scope.grouping = { groupedColumns: ["ShipCountry", "CustomerID"] };
                $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
            });
    </script>
</body>
</html>

{% endhighlight %}

![Grouping customization of angular grid](Getting-started_images/Getting-started_img6.png)
{:.image }

## Add Summaries

`Summaries` can be added by setting the `e-showsummary` to true and adding required summary rows and columns in the `e-summaryrows` property. You can set value for the `e-summaryrows` and that value can be accessed through $scope variable. For demonstration, stock column's sum value is displayed as summary.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="listCtrl">
<head>
    <title>Essential Studio for AngularJS: Flat Grid</title>
</head>
<body ng-controller="SummaryCtrl">
    <div id="Grid" ej-grid e-datasource="data" e-columns="cols" e-allowpaging="true" e-pagesettings-pagesize="8" e-allowgrouping="true" e-groupsettings="grouping" e-showsummary="true" e-summaryrows="summaryRows">
    </div>
    <script>
        angular.module('listCtrl', ['ejangular'])
       .controller('SummaryCtrl', function ($scope) {
           //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
           $scope.data = window.gridData;
           $scope.cols = ["OrderID", "EmployeeID", "CustomerID", "ShipCountry", "Freight"];
           $scope.grouping = { groupedColumns: ["CustomerID"] };
           $scope.summaryRows = [
                            { title: "Sum", summaryColumns: [{ summaryType: ej.Grid.SummaryType.Sum, displayColumn: "Freight", dataMember: "Freight" }] },
           ];
       });
    </script>
</body>
</html>

{% endhighlight %}

![Summary rows added in angular grid](Getting-started_images/Getting-started_img7.png)
{:.image }


