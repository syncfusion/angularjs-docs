---
layout: post
title: User-Interaction
description: user interaction
platform: AngularJS
control: Maps
documentation: ug
---

# User Interaction

Options like zooming, panning, and map selection enables the effective interaction on Map elements.

## Map Selection

Each shape in the Map can be selected and deselected during interaction with the shapes. 

The `e-shapesettings-selectionColor` property is used to get or set the selected shape color. The `e-shapesettings-selectionStroke` and `e-shapesettings-selectionStrokeWidth` properties are used to customize the selected shape border.

You can select the shape by tapping the shape. The Single selection is enabled by the `e-enableSelection` property of shape layer. When `e-enableSelection` is set to false, the shapes cannot be selected. 

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map>
        <e-layers>
            <e-layer e-shapedata=usMap e-enableselection="true" e-shapesettings-fill="#9CBF4E" 
            e-shapesettings-strokeThickness="0.5" e-shapesettings-stroke="white"
            e-shapesettings-selectionStrokeWidth="2" e-shapesettings-selectionStroke="white"
            e-shapesettings-selectionColor="#BC5353"></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>

{% endhighlight %}

![](User-Interaction_images/User-Interaction_img1.png)


## MultiSelection


This feature enables you to select multiple Map shapes on mouse taps accompanied by the "**Control**" key press. To enable this feature, set the `e-selectionMode` property as "**multiple**" along with the `e-enableSelection` property.

{% highlight html %}

   <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map>
        <e-layers>
            <e-layer e-shapedata=usMap e-enableselection="true" e-selectionmode="multiple"></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>   


{% endhighlight %}

![](User-Interaction_images/User-Interaction_img5.png)


## Dragging On Selection

This feature enables you to select the shapes by dragging over the shapes. While dragging over the shapes, a rectangle is generated and the shapes that comes within the rectangle is selected.
You can enable this feature by setting the `e-draggingOnSelection` property  **True**.

{% highlight html %}

 <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map>
        <e-layers>
            <e-layer e-draggingonselection="true"></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>   

     

{% endhighlight %}


![](User-Interaction_images/User-Interaction_img1.png)


## Zooming

The zooming feature enables you to zoom in and out the Map to show in-depth information. It is controlled by the `e-zoomsettings-level` property of the Map. When the zoom level of the Map control is increased, the Map is zoomed in. When the zoom level is decreased, then the Map is zoomed out.

### Properties

The following properties are related to the zooming feature of the **Maps** control:

1. level

2. enableZoom

3. minValue

4. maxValue

### Level

The `e-zoomSettings-level` property determines the Map’s scale size when zooming. The default value of `level` is 1. 

N> level cannot be less than 1

### EnableZoom

The `e-zoomSettings-enableZoom` property enables or disables the zooming feature. 

### MinValue

The `e-zoomSettings-minValue` property is used to set the minimum zoom level of the Map. 

### MaxValue

The `e-zoomSettings-maxValue` property is used to set the maximum zoom level of the Map.

{% highlight html %}

 <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map e-zoomsettings-enablezoom="true" 
      e-zoomsettings-minValue="1" e-zoomsettings-maxValue="20" e-zoomsettings-level="1">
        <e-layers>
            <e-layer e-shapedata=usMap ></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>   



{% endhighlight %}

### Factor

Specifies the zoom factor for map zoom value, you can use `factor` property.

{% highlight html %}

 <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map e-zoomsettings-enablezoom="true" 
      e-zoomsettings-minValue="1" e-zoomsettings-maxValue="20" e-zoomsettings-factor="1">
        <e-layers>
            <e-layer e-shapedata=usMap ></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>   



{% endhighlight %}


### Additional Options to Zoom the Map

Maps can be zoomed by using the following options also,

* Zoom method.
* mouse scroll.
* mouse double tap.
* shape selection
* Position

### Zoom method

You can zoom the Maps by using `zoom` method. The `zoom` method contains parameter zoom value. The Map can be zoomed or scaled based on zoom value parameter.

{% highlight html %}
 
        $("#map").ejMap("zoom", 2);


{% endhighlight %}

### Mouse scroll

You can zoom the Map with mouse events by using mouse scroll. When the mouse is scrolled up, the Map is zoomed in and when the mouse is scrolled down, the Map is zoomed out.

### Mouse double tap

When the Map is double-tapped by using mouse, the zoom in operation is performed. 

![](User-Interaction_images/User-Interaction_img2.png)

### Shape Selection

Map shape is zoomed to the whole Map area on the shape selected. Animation can be applied for that zooming by using the `e-enableAnimation` property as true. 

You can enable this feature by setting `e-zoomSettings-enableZoomOnSelection` property value as ‘_True_’. 

When `e-zoomSettings-enableZoomOnSelection` property is set to true, then zooming by double click is muted.

{% highlight html %}

 <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-zoomsettings-enableZoomOnSelection="true">
        <e-layers>
            <e-layer e-shapedata=usMap ></e-layer>
        </e-layers>
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html> 
      

{% endhighlight %}

### Positioning

Depending on the latitude and longitude, you can zoom the Map to the exact position. All locations are considered as latitude and longitude values and the exact location is considered as Map coordinates.

The `navigateTo` is a method that allows you to zoom the Map control to the given location. This method contains three attributes as follows.

<table>
<tr>
<th>
Attribute</th><th>
Type</th><th>
Description</th></tr>
<tr>
<td>
Latitude</td><td>
Double</td><td>
Latitude point of the position </td></tr>
<tr>
<td>
Longitude</td><td>
Double</td><td>
Longitude point of the position</td></tr>
<tr>
<td>
level</td><td>
Double</td><td>
Zoom level of the map</td></tr>
</table>


{% highlight html %}

    <script type="text/html">
        function buttonClick() {
            $("#map").ejMap("navigateTo", 13, 80, 5);
        }
    </script> 

{% endhighlight %}

## Panning

The panning feature enables the Map navigation. The `e-enablepan` property is used to enable or disable the panning support.

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map e-enablepan="true">
      </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>

{% endhighlight %}

## Navigation Control

**Navigation** control is built-in with **Maps** control. With Navigation control, **Maps** can be panned in any direction and zoomed. It is possible to show or hide the NavigationControl by `e-enablenavigation` property.


![](User-Interaction_images/User-Interaction_img3.png)



{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-navigationcontrol-enableNavigation="true">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>

{% endhighlight %}

### Positions

The Navigation control can be positioned in two ways.

* Absolute Position
* Dock Position

#### Absolute Position

Based on the margin values of X and Y-axes, the navigation control can be positioned with the help of the **x** and **y** properties available in `e-navigationControl-absolutePosition`. For positioning the navigation control based on margins corresponding to a Map, `e-navigationControl-dockPosition` value is set as ‘_none_’.

#### Dock Position

The navigation control can be positioned in the following locations within the container.

* topLeft
* topCenter
* topRight
* centerLeft
* center
* centerRight
* bottomLeft
* bottomRight
* bottomCenter
* bottomRight
* none

You can set this option by using `e-navigationControl-dockPosition` 

{% highlight html %}

 <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-navigationcontrol-enableNavigation="true" e-navigationcontrol-orientation="vertical" 
      e-navigationcontrol-dockPosition="none" e-navigationcontrol-absolutePosition-x="5"
      e-navigationcontrol-absolutePosition-y="16">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>
   	


{% endhighlight %}

#### Orientation

Set the `orientation` value for navigation control.

<table class="params">
	<thead>
		<tr>
			<th>Name </th>			
			<th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="name">horizontal</td>			
			<td class="description">specifies the horizontal position</td>
		</tr>
		<tr>
			<td class="name">vertical</td>			
			<td class="description">specifies the vertical position</td>
		</tr>
	</tbody>
</table>


{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-navigationcontrol-enableNavigation="true" e-navigationcontrol-orientation="vertical">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>
   	
   
{% endhighlight %}

#### Content


Specifies the navigation control template for map, you can use `content` property.


{% highlight html %}
 
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-navigationcontrol-enableNavigation="true" e-navigationcontrol-content="">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>

{% endhighlight %}



### Animation

 **Animation** is enabled or disabled using `enable animation`property. 

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-enableanimation="true">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>

{% endhighlight %}


#### Enable Layer Change Animation 

Enables or Disables the animation for layer change in map, you can use `enableLayerChangeAnimation` property and the default value is false.


{% highlight html %}
 
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-enablelayerchangeanimation="">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>    

{% endhighlight %}


### Responsiveness during browser resize

**Map** is made responsive when resizing the browser by using `isResponsive` property.

{% highlight javascript %}

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="MapsApp">
    <head>
        <title>Essential Studio for AngularJS: Maps</title>
        <!--CSS and Script file References -->
    </head>
    <body ng-controller="MapsCtrl">
      <div id="mapContainer" style="width: 900px; height: 600px;" ej-map 
      e-isResponsive="true">      
    </div>
    <script>
        angular.module('MapsApp', ['ejangular'])
        .controller('MapsCtrl', function ($scope) {
                        });
    </script>
    </body>
</html>    

{% endhighlight %}




