---
layout: post
title: Getting-Started
description: getting started
platform: AngularJS
control: DateTimePicker
documentation: ug
---

# Getting Started

This section explains briefly about how to create a **DateTimePicker** in your application with **JavaScript**.

**Essential JavaScript DateTimePicker** provides support to display a calendar within a web page and allows you to pick a date and time from the calendar. In this example, you can learn how to customize **DateTimePicker** in a real-time application for an appointment and to choose current time for one week. 

The following screenshot illustrates the functionality of a **DateTimePicker** with date range of maximum one week.

![](/js/DateTimePicker/Getting-Started_images/Getting-Started_img1.png)


## Create DateTimePicker 

The **DateTimePicker** widget has built-in features such as keyboard navigation, other navigation with animations and flexible APIs. You can easily create the **DateTimePicker** widget by using simple input **&lt;textbox&gt;** element as follows.

1. Create an HTML file and add required scripts and CSS files to render the Essential JavaScript component as given in the [Getting Started](https://help.syncfusion.com/js/control-initialization).
2. Essential JavaScript includes angular directives for all controls with the ej.widget.angular.min.js script file. All the Essential JS directives have been encapsulated into a single module called **ejangular**. To render our ej controls in angular, you need to refer the “angular.min.js” and “ej.widget.angular.min.js” in your application.

{% highlight html %}

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" ng-app="DateTimeCtrl">
   <head>
      <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8" />
      <!-- Style sheet for default theme (flat azure) -->
      <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
      <!--Scripts-->
      <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"> </script>
      <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
      <!--Add custom scripts here -->
   </head>
   <body ng-controller="DateTimeCtrller">
      <!-- add DateTimePicker element here -->
   </body>
</html>

{% endhighlight %}

N> jQuery.easing external dependency has been removed from version 14.3.0.49 onwards. Kindly include this jQuery.easing dependency for versions lesser than 14.3.0.49 in order to support animation effects.

The ng-app directive explains the root element (<html> or <body> tags) of the application. You will assign a name to the ng-app directive, then you must create a module with that name. In this module, you will have to define your directives, services, filters and configurations.

Properties can be bind to ejDateTimePicker control using the prefix e- and particular property name as shown as below

Add **&lt;input&gt;** element to render a **DateTimePicker**.

{% highlight html %}

<div class="content-container-fluid">
   <div class="row">
      <div class="cols-sample-area">
         <div class="frame">
            <div class="control">
               <input type="text" id="dateTime1" ej-datetimepicker e-value="value" e-width="width" />
            </div>
         </div>
      </div>
   </div>
</div>

{% endhighlight %}



Add the following styles to show the **DateTimePicker** control in the horizontal order.


{% highlight css %}

<style type="text/css" class="cssStyles">
   .control {
         margin: 0 auto;
         width: 210px;
   }
</style>

{% endhighlight %}

Add the following in script section.

{% highlight javascript %}
        angular.module('DateTimeCtrl', ['ejangular'])
           .controller('DateTimePickerCtrl', function ($scope) {
               $scope.value =new date();
			   $scope.width="180px";
           });
{% endhighlight %}



The following screenshot displays a **DateTimePicker** control.

![](/js/DateTimePicker/Getting-Started_images/Getting-Started_img2.png)

## Set the Min and Max Date with Time Interval

In a real-time appointment scenario, the appointment is open only for a limited number of days. You have to select a date and time within the given range. This can be achieved by using the properties **min** and **max** that enables the specified date range in the **DateTimePicker** control.

{% highlight html %}

<input type="text" id="dateTime1" ej-datetimepicker e-value="value" e-width="width" />

{% endhighlight %}


{% highlight javascript %}
        angular.module('DateTimeCtrl', ['ejangular'])
           .controller('DateTimePickerCtrl', function ($scope) {
               $scope.value =new date();
			   $scope.width="180px";
               $scope.mindate = "9/23/2014 9:00 AM";
			   $scope.maxdate = "9/29/2014 2:00 PM";
           });
{% endhighlight %}




The following screenshot shows the output for the above code example.

![](/js/DateTimePicker/Getting-Started_images/Getting-Started_img3.png)

