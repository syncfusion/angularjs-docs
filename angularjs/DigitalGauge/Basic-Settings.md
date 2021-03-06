---
layout: post
title: Basic-Settings
description: basic settings
platform: AngularJS
control: Digital Gauge
documentation: ug
---

# Basic Settings

## Height and Width Customization

The basic customization for any control is to set the dimension. Here dimension refers to two major attributes such as **height** and **width**. The **height** and **width** assigned in the control will render the canvas element in the given size. The code example to set **height** and **width** is as follow.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="DigitalGaugeApp">
    <head>
        <title>Essential Studio for AngularJS: DigitalGauge</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="DigitalGaugeCtrl">
        <div id="digitalframe">
                 <ej-digitalgauge e-height="200" e-width="500" e-value="Syncfusion"></ej-digitalgauge>
        </div>
         <script>
        angular.module('DigitalGaugeApp', ['ejangular'])
        .controller('DigitalGaugeCtrl', function ($scope) {
         });
    </script>
    </body>
</html>



{% endhighlight %}



Execute the above code examples to render the **Digital****Gauge** as follows. 

![](Basic-Settings_images/Basic-Settings_img1.png)



## Responsive Layout

* For any display devices, the control will be rendered based on the space available in that device. For this purpose, **resizing** property is given to the **Digital Gauge** control. The **Digital Gauge** renders with a given value. 

* When the browser resize the canvas element checks the dimension with its parent element. If there are any changes in parent dimension, **Gauge** control will changes the dimension based on its parent element change. This feature is enabled by using the property **isResponsive.**


{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="DigitalGaugeApp">
    <head>
        <title>Essential Studio for AngularJS: DigitalGauge</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="DigitalGaugeCtrl">
        <div id="digitalframe">
                 <ej-digitalgauge  e-width="800" e-isresponsive="true"></ej-digitalgauge>
        </div>
        <script>
        angular.module('DigitalGaugeApp', ['ejangular'])
        .controller('DigitalGaugeCtrl', function ($scope) {
         });
    </script>
    </body>
</html>

{% endhighlight %}



Execute the above code examples to render the **Digital****Gauge** as follows. 

![](Basic-Settings_images/Basic-Settings_img2.png)



## Themes

**Themes** give the good appearance to the control. There are two types of **Themes** available for **Digital****Gauge** as follows

* flatlight

* flatdark

{% highlight html %}


<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="DigitalGaugeApp">
    <head>
        <title>Essential Studio for AngularJS: DigitalGauge</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="DigitalGaugeCtrl">
        <div id="digitalframe">
                 <ej-digitalgauge e-width="800" e-isresponsive="true" e-themes="flatdark"
                  e-value="LOS ANGELS 40 KM"></ej-digitalgauge>
        </div>
        <script>
        angular.module('DigitalGaugeApp', ['ejangular'])
        .controller('DigitalGaugeCtrl', function ($scope) {
         });
    </script>
    </body>
</html>


{% endhighlight %}



Execute the above code examples to render the **Digital****Gauge** as follows. 

![](Basic-Settings_images/Basic-Settings_img3.png)



