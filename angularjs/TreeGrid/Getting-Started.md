---
layout: post
title: Getting-Started
description: getting started
platform: AngularJS
control: TreeGrid
documentation: ug
---

# Getting Started

## Create your first tree grid in AngularJS

The **Essential JavaScript tree grid** has been designed to represent and edit the hierarchical data. 

This section explains how to create the tree grid widget in your application with hierarchical data source and enable sorting and editing. The following screenshot displays the output: 

![](/angularjs/TreeGrid/Getting-Started_images/Getting-Started_img1.png)                                                     

1.Create a HTML file and add the following template.     

{% highlight html %}

 <!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
   <meta name="viewport"content="width=device-width, initial-scale=1.0"/>
   <meta charset="utf-8" />
   <link href=" http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet"/>
   <script src="http://cdn.syncfusion.com/js/assets/external/angular.min.js"></script>
   <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>
   <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
   <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>
   <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>
   <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
   <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/common/ej.widget.angular.min.js"></script>
</head>
<body>
   <!--Add TreeGrid control here -->
</body>
</html>

{% endhighlight %}

2.Add the **&lt;div&gt;** element within the **&lt;Body&gt;** tag.

{% highlight html %}

<!doctype html>
<html lang="en" ng-app="listCtrl">
   <head>
      //...
   </head>
   <body ng-controller="TreeGridCtrl">
      <!--Add  TreeGrid control here-->    
      <div id="TreeGridContainer" ej-treegrid
         e-columns="columns">             
      </div>
      <script>
         var columns=[                    
               { field: "taskName", headerText: "Task Name" },
               { field: "startDate", headerText: "Start date"},
               { field: "endDate", headerText: "End Date" },
               { field: "duration", headerText: "Duration"},
               { field: "progress", headerText: "Progress"}
           ];
         angular.module('listCtrl', ['ejangular'])
         .controller('TreeGridCtrl', function ($scope) {
          //Initialize gantt datasource created in the last step
          $scope.columns = columns;
         });
      </script>  
   </body>
</html>

{% endhighlight %}

In the previous code sample, the `ej-treegrid` denotes the control directive for the Syncfusion's tree grid angular widget and all its properties are prefixed with the letter `e-` (For example, e-datasource.)

![](/angularjs/TreeGrid/Getting-Started_images/Getting-Started_img2.png)            

TreeGrid with empty datasource 
{:.caption}

3.Create data source for tree grid.

{% highlight js %}

        var treeGridDataSource = [{
    taskID: 2,
    taskName: "Planning",
    startDate: "02/03/2014",
    endDate: "02/07/2014",
    duration: 10,
    progress: 56,
    subtasks: [{
        taskID: 3,
        taskName: "Plan timeline",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 4,
        taskName: "Plan budget",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 5,
        taskName: "Allocate resources",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 6,
        taskName: "Planning complete",
        startDate: "02/07/2014",
        endDate: "02/07/2014",
        duration: 0,
        progress: 40
    }]
}, {
    taskID: 7,
    taskName: "Design",
    startDate: "02/10/2014",
    endDate: "02/14/2014",
    duration: 10,
    progress: 76,
    subtasks: [{
        taskID: 8,
        taskName: "Software Specification",
        startDate: "02/10/2014",
        endDate: "02/12/2014",
        duration: 3,
        progress: "60"
    }, {
        taskID: 9,
        taskName: "Develop prototype",
        startDate: "02/10/2014",
        endDate: "02/12/2014",
        duration: 3,
        progress: "100"
    }, {
        taskID: 10,
        taskName: "Get approval from customer",
        startDate: "02/13/2014",
        endDate: "02/14/2014",
        duration: 2,
        progress: "100"
    }, {
        taskID: 11,
        taskName: "Design complete",
        startDate: "02/14/2014",
        endDate: "02/14/2014",
        duration: 0,
        predecessor: "10FF",
        progress: 65
    }]
}];

{% endhighlight %}

4.Initialize the tree grid with data source created in the previous step.                     

{% highlight js %}

 <body ng-controller="TreeGridCtrl">
   <!--Add  TreeGrid control here-->    
   <div id="TreeGridContainer" ej-treegrid
      e-dataSource="treeGridDataSource"
      e-childMapping="subtasks"
      e-columns="columns">             
   </div>
   <script>
      var columns=[                    
            { field: "taskName", headerText: "Task Name" },
            { field: "startDate", headerText: "Start date"},
            { field: "endDate", headerText: "End Date" },
            { field: "duration", headerText: "Duration"},
            { field: "progress", headerText: "Progress"}
        ];
      angular.module('listCtrl', ['ejangular'])
      .controller('TreeGridCtrl', function ($scope) {
       //Initialize gantt with datasource created in the last step
       $scope.treeGridDataSource=treeGridDataSource;
       $scope.columns = columns;
      });
   </script>  
</body>     
    
{% endhighlight %}

The tree grid widget is displayed as the output in the following screenshot:         

![](/angularjs/TreeGrid/Getting-Started_images/Getting-Started_img3.png) 

## Enable Sorting

The tree grid control has sorting functionality to arrange the data in ascending or descending order based on a particular column.

### Multicolumn Sorting

Enable the multicolumn sorting in tree grid by setting the [`e-allowMultiSorting`](http://help.syncfusion.com/js/api/ejtreegrid#allowmultisorting "allowMultiSorting") to `true`. You can sort multiple columns in the tree grid by selecting the desired column header while holding the `Ctrl` key.           

{% highlight js %}                 

<body ng-controller="TreeGridCtrl">
   <!--Add  TreeGrid control here-->    
   <div id="TreeGridContainer" ej-gantt
      e-allowSorting="true"
      e-allowMultiSorting="true">             
   </div>
   <script>
      angular.module('listCtrl', ['ejangular'])
        .controller('TreeGridCtrl', function ($scope) {
          //...
        });
        
   </script>  
</body>    

{% endhighlight %}

![](/angularjs/TreeGrid/Getting-Started_images/Getting-Started_img4.png)

## Enable Editing

You can enable Editing in tree grid by using the [`e-editSettings`](http://help.syncfusion.com/js/api/ejtreegrid#editsettings "editSettings") property. The following code sample demonstrates this.

{% highlight js %}
 <body ng-controller="TreeGridCtrl">
   <!--Add  TreeGrid control here-->    
   <div id="TreeGridContainer" ej-gantt
      e-editSettings="editSettings">             
   </div>
   <script>
      var editSettings=  {
       allowEditing: true,
       editMode: "cellEditing"
      };
      angular.module('listCtrl', ['ejangular'])
      .controller('TreeGridCtrl', function ($scope) {
      $scope.editSettings=editSettings;
      });
   </script>  
</body> 
    
{% endhighlight %}

The following editors are provided for support in the tree grid control.            

* String
* Boolean
* Numeric
* Dropdown
* Datepicker
* Datetimepicker                

You can set the editor type for a particular column as follows.

{% highlight js %}

<body ng-controller="TreeGridCtrl">
   <!--Add  TreeGrid control here-->    
   <div id="TreeGridContainer" ej-gantt
      e-columns="columns">             
   </div>
   <script>
      var columns=[{
       field: "startDate",
       headerText: "Start Date",
       editType: "datepicker"
      }, {
       field: "endDate",
       headerText: "End Date"
      }, {
       field: "duration",
       headerText: "Duration",
       editType: "numericedit"
      }, ];
      angular.module('listCtrl', ['ejangular'])
      .controller('TreeGridCtrl', function ($scope) {
       //Initialize gantt with datasource created in the last step
       $scope.columns = columns;
      });
   </script>  
</body>
   
{% endhighlight %}
                                     
The output of the DateTimePicker editor in the tree grid control is as follows:

![](/angularjs/TreeGrid/Getting-Started_images/Getting-Started_img5.png)                                                              

