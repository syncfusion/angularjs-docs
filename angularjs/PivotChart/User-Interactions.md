---
layout: post
title: User-Interactions
description: user interactions
platform: AngularJS
control: pivotchart
documentation: ug
keywords: ejpivotchart, pivotchart, pivotchart widget, js pivotchart 
---

# User Interactions

## Tooltip

### Enable Tooltip for Data Points
Tooltip for the data points can be enabled by using the **"visible"** option of the [`tooltip`](/api/js/ejchart#members:commonseriesoptions-tooltip-visible) property under **"commonSeriesOptions"** of PivotChart.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                //....
                //Enabling tooltip for data points
                tooltip:
                {
                    visible: true
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/tooltip.png) 

### Tooltip Template
HTML elements can be displayed inside the tooltip by using the [`template`](/api/js/ejchart#members:commonseriesoptions-tooltip-template) option. The template option takes the value of the “id” attribute from the HTML element. You can use the **#point.x#** and **#point.y#** as place holders in the HTML element to display the X and Y values of the corresponding data points.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions"/>
        <div id="Tooltip" style="display: none;">
        <label id="cc1">In </label>
        <label id="fyvalue">&nbsp;#point.x# </label>
        <label id="cc2">, customer count is</label>
        <label id="ccvalue">&nbsp;#point.y# </label>
    </div>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                //....
                //Enabling tooltip for data points
                tooltip:
                {
                    visible: true,
                    template: 'Tooltip'
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/tooltiptemplate.png) 

### Tooltip Customization
By using [`fill`](/api/js/ejchart#members:commonseriesoptions-tooltip-fill) and [`border`](/api/js/ejchart#members:commonseriesoptions-tooltip-border) properties of tooltip, you can customize its background color, border color and border width.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions"/>
        <div id="Tooltip" style="display: none;">
        <label id="cc1">In </label>
        <label id="fyvalue">&nbsp;#point.x# </label>
        <label id="cc2">, customer count is</label>
        <label id="ccvalue">&nbsp;#point.y# </label>
    </div>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                //....
                //Enabling tooltip for data points
                tooltip:
                {
                    visible: true,
                    //Customize tooltip background color and border
                    fill: '#FF9933',
                    border:
                    {
                        width: 1,
                        color: "#993300"
                    }
                }
            };
        });
    </script>
</body>

{% endhighlight %}   

![](User-Interactions_images/tooltipcustomization.png) 

### Tooltip with Rounded Corners
The tooltip properties, [`rx`](/api/js/ejchart#members:commonseriesoptions-tooltip-rx) and [`ry`](/api/js/ejchart#members:commonseriesoptions-tooltip-ry) are used to customize its corner radius.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                //....
                //Enabling tooltip for data points
                tooltip:
                {
                    visible: true,
                    //Customize the corner radius of the tooltip rectangle
                    rx: "20",
                    ry: "20"
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/tooltiprounded.png) 

## Zooming and Panning

### Enable Zooming

There are two ways to zoom the Chart:

* When [`zooming.enable`](/api/js/ejchart#members:zooming-enable) option is set to true, you can zoom the Chart by using rubber band selection.
* When [`zooming.enableMouseWheel`](/api/js/ejchart#members:zooming-enablemousewheel) option is set to true, you can zoom the Chart on mouse wheel scrolling.

{% highlight javascript %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-zooming="zooming"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.zooming = {
                //Enable zooming in Chart
                zooming:
                {
                    enable: true
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/zooming.png) 

After zooming the Chart, a zooming toolbar will appear with options to *zoom, pan and reset*. Selecting the **“Pan”** option will allow to view the Chart and selecting the **“Reset”** option will reset the zoomed Chart.

![](User-Interactions_images/pan.png) 

### Types of Zooming
You can zoom the particular axis like horizontal axis or vertical axis or both axis using [`type`](/api/js/ejchart#members:zooming-type) option in zooming. 

N> By default, the value for the `type` option in zooming is “x,y” (indicating both axis) in PivotChart.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-zooming="zooming"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.zooming = {
                //....
                //Enable zooming in Chart
                zooming:
                {
                    enable: true,
                    //Enable horizontal zooming
                    type: 'x'
                }
            };
        });
    </script>
</body>

{% endhighlight %}

### Enable Scrollbar

* When [`zooming.enableScrollbar`](/api/js/ejpivotchart#members:zooming-enablescrollbar) option is set to true, the PivotChart is rendered along with the scroll bars for precise view of data. The data can be viewed by using scroll bar or by using mouse wheel scrolling.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-zooming="zooming"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.zooming = {
                //Enable zooming in Chart
                zooming:
                {
                    enableScrollbar: true
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/scrollbar.png)

## Marker and Crosshair

### Marker Shape Customization
In PivotChart, you can customize the marker [`shape`](/api/js/ejchart#members:series-marker-shape) with the following symbols.

* Rectangle
* Circle
* Cross
* Diamond 
* Pentagon
* Hexagon
* Star
* Ellipse
* Triangle etc.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Line
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++) 
                this.model.series[seriescount].marker.shape = "Triangle";
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/marker.png) 

### Enable Crosshair and Crosshair Label
Crosshair helps you to view the value at mouse position or touch contact point. Crosshair can be enabled by using the [`visible`](/api/js/ejchart#members:crosshair-visible) option in `e-crosshair` property. Crosshair label can be enabled by using the **“visible”** option in [`crosshairLabel`](/api/js/ejchart#members:primaryxaxis-crosshairlabel) property within its corresponding axis.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-crosshair="crosshair" e-primaryXAxis="primaryXAxis" e-primaryYAxis="primaryYAxis"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            //Initializing Crosshair
            $scope.crosshair = {
                visible: true
            };
            $scope.primaryXAxis = {
                //Enable Crosshair Label in X-Axis
                crosshairLabel:
                {
                    visible: true
                }
            };
            $scope.primaryYAxis = {
                //Enable Crosshair Label to Y-Axis 
                crosshairLabel:
                {
                    visible: true
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/crosshair.png) 

### Crosshair Line and Label Customization
By using [`line`](/api/js/ejchart#members:crosshair-line) property of crosshair, you can customize its line color and width. Also by using `fill` and `border` properties of [`crosshairLabel`](/api/js/ejchart#members:primaryxaxis-crosshairlabel) in its corresponding axis , you can customize its background color, border color and border width.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-crosshair="crosshair" e-primaryXAxis="primaryXAxis" e-primaryYAxis="primaryYAxis"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            //Initializing Crosshair
            $scope.crosshair = {
                visible: true,
                //Customizing the crosshair line
                line:
                {
                    color: 'gray',
                    width: 2
                }
            };
            $scope.primaryXAxis = {
                //Enable Crosshair Label in X-Axis 
                crosshairLabel:
                {
                    visible: true,
                    //Customizing the crosshair label background color and border
                    fill: "red",
                    border:
                    {
                        color: "green",
                        width: 2
                    }
                }
            };
            $scope.primaryYAxis = {
                //Enable Crosshair Label in Y-Axis
                crosshairLabel:
                {
                    visible: true
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/crosshairline.png) 

## Trackball

### Enable trackball
Trackball can be enabled by setting both - ['visible'](/api/js/ejchart#members:crosshair-visible) option of the crosshair to true and [`type`](/api/js/ejchart#members:crosshair-type) option of the crosshair to **“trackball”.** The default value of type is **“crosshair”.**

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-crosshair="crosshair"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            //Initializing Crosshair
            $scope.crosshair = {
                visible: true,
                //Change crosshair type to trackball
                type: 'trackball'
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/trackball.png) 

### Trackball Marker and Line Customization
Shape and size of the trackball marker can be customized using the [`shape`](/api/js/ejchart#members:commonseriesoptions-marker-shape) and [`size`](/api/js/ejchart#members:crosshair-marker-size) options of the crosshair marker. Color and width of the trackball line can be customized using the **“line”** option in the crosshair.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-crosshair="crosshair"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            //Initializing Crosshair
            $scope.crosshair = {
                visible: true,
                //Change crosshair type to trackball
                type: 'trackball',
                //Customize the trackball line color and width
                line:
                {
                    color: '#800000',
                    width: 2
                },
                //Customize the trackball marker shape, size and visibility
                marker:
                {
                    shape: 'pentagon',
                    size:
                    {
                        height: 9,
                        width: 9
                    },
                    visible: true
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/trackballmarker.png) 

## Highlight
PivotChart provides highlighting support for the series and data points on mouse hover. To enable highlighting, set the **“enable”** property to true in the [`highlightsettings`](/api/js/ejchart#members:series-highlightsettings-enable) option of the series.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++) 
                this.model.series[seriescount].highlightSettings.enable = true
            };
        });
    </script>
</body>

{% endhighlight %} 

### Highlight Mode
You can set three different modes for highlighting data points and series by using the [`mode`](/api/js/ejchart#members:series-highlightsettings-mode) property of the [`highlightsettings`](/api/js/ejchart#members:series-highlightsettings).
 
* series
* points
* cluster

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].highlightSettings.enable = true;
                    this.model.series[seriescount].highlightSettings.mode = "series";
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/highlightmode.png) 

### Customize the Highlight Styles
To customize the highlighted series, use [`border.color`](/api/js/ejchart#members:series-highlightsettings-border-color), [`border.width`](/api/js/ejchart#members:series-highlightsettings-border-width) and [`opacity`](/api/js/ejchart#members:series-highlightsettings-opacity)
 options in the [`highlightSettings`](/api/js/ejchart#members:series-highlightsettings) property.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].highlightSettings.enable = true;
                    this.model.series[seriescount].highlightSettings.opacity = "0.5";
                    this.model.series[seriescount].highlightSettings.border.width = "1.5";
                    this.model.series[seriescount].highlightSettings.border.color = "red";
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/customizehighlight.png) 

### Patterns to Highlight
PivotChart provides pattern support for highlighting the data by setting an appropriate value to the [`pattern`](/api/js/ejchart#members:series-highlightsettings-pattern) property of the [`highlightSettings`](/api/js/ejchart#members:series-highlightsettings). The different types of highlight patterns are as follows.

* chessboard
* crosshatch
* dots
* packman
* grid
* turquoise
* star
* triangle
* circle
* tile
* horizontalDash
* verticalDash
* rectangle
* box
* verticalStripe
* horizontalStripe
* bubble
* diagonalBackward
* diagonalForward


{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].highlightSettings.enable = true;
                    this.model.series[seriescount].highlightSettings.pattern = "chessboard";
                }
            };
        });
    </script>
</body>

{% endhighlight %} 

![](User-Interactions_images/patternhighlight.png) 

## Selection
PivotChart provides selection support for the series and data points on mouse click. To enable selection, set the **“enable”** property to true in the [`selectionSettings`](/api/js/ejchart#members:series-selectionsettings-enable) option of the series.

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].selectionSettings.enable = true;
                }
            };
        });
    </script>
</body>

{% endhighlight %}

### Selection Mode

You can set three different selection mode for highlighting the data points and series by using the [`mode`](/api/js/ejchart#members:series-selectionsettings-mode) property of the [`selectionSettings`](/api/js/ejchart#members:series-selectionsettings).

* series
* points
* cluster

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].selectionSettings.enable = true;
                    this.model.series[seriescount].selectionSettings.mode = "series";
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/selectionmode.png) 

### Customize the Selection Styles
To customize the selection styles, use the [`border.color`](/api/js/ejchart#members:commonseriesoptions-selectionsettings-border-color), [`border.width`](/api/js/ejchart#members:commonseriesoptions-selectionsettings-border-width) and [`opacity`](/api/js/ejchart#members:commonseriesoptions-selectionsettings-opacity) options in the [`selectionSettings`](/api/js/ejchart#members:series-selectionsettings).

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].selectionSettings.enable = true;
                    this.model.series[seriescount].selectionSettings.border.width = "1.5";
                    this.model.series[seriescount].selectionSettings.border.color = "red";
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/customizeselection.png) 

### Patterns for Selection
PivotChart provides pattern support for the selecting the data by setting an appropriate value to the [`pattern`](/api/js/ejchart#members:series-selectionsettings-pattern) property of the [`selectionSettings`](/api/js/ejchart#members:series-selectionsettings) option. The different types of selection patterns are as follows.

* chessboard
* crosshatch
* dots
* packman
* grid
* turquoise
* star
* triangle
* circle
* tile
* horizontalDash
* verticalDash
* rectangle
* box
* verticalStripe
* horizontalStripe
* bubble
* diagonalBackward
* diagonalForward

{% highlight html %}

<body>
    <div ng-controller="PivotChartCtrl">
        <div id="PivotChart1" ej-pivotchart e-commonSeriesOptions="commonSeriesOptions" e-seriesRendering="seriesRendering"/>
    </div>
    <script>
        angular.module('PivotChartApp', ['ejangular']).controller('PivotChartCtrl', function ($scope) {
            ///..
            $scope.commonSeriesOptions = {
                type: ej.PivotChart.ChartTypes.Column
            };
            $scope.seriesRendering = function(args){
                for (var seriescount = 0; seriescount < this.model.series.length; seriescount++)
                {
                    this.model.series[seriescount].selectionSettings.enable = true;
                    this.model.series[seriescount].selectionSettings.pattern = "chessboard";
                }
            };
        });
    </script>
</body>

{% endhighlight %}

![](User-Interactions_images/patternselecion.png) 
