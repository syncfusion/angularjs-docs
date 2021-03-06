---
layout: post
title: Getting-Started
description: getting started
platform: AngularJS
control: ColorPicker
documentation: ug
---

# Getting Started

This section explains briefly about how to create a **ColorPicker** in your application with **JavaScript**. The **Essential JavaScript ColorPicker** control provides you support for selecting the colors in different sources such as palettes, picker or custom palettes. You can also render the color value from control in three formats such as RGB, HSV and HEXCODE. 

In this example, you can learn how to customize **ColorPicker** control in a category Application. 

![](Getting-Started_images/Getting-Started_img1.png) 

## Create ColorPicker Control

Use the following steps to create the **ColorPicker** control.

1. Create an HTML file and add required scripts and CSS files to render the Essential JavaScript component as given in the [Getting Started](https://help.syncfusion.com/js/control-initialization).

2. Essential JavaScript includes angular directives for all controls with the ej.widget.angular.min.js script file. All the Essential JS directives have been encapsulated into a single module called **ejangular**. To render our ej controls in angular, you need to refer the “angular.min.js” and “ej.widget.angular.min.js” in your application.

{% highlight html %}

<!DOCTYPE html>
    <html xmlns="http://www.w3.org/1999/xhtml" ng-app="ColorPickCtrl">
    <head>
        <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8" />
        <title>Getting Started Essential JS</title>
        <!-- Style sheet for default theme (flat azure) -->
        <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
        <!--Scripts-->
        <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>
        <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js"></script>
        <!--Add custom scripts here -->
    </head>
    <body ng-controller="ColorPickCtrller">
        <input id="CategoryColor" ej-colorpicker e-value="#278787" />
        <!--add the ColorPicker element here -->
    </body>
    </html>

{% endhighlight %}

N> jQuery.easing external dependency has been removed from version 14.3.0.49 onwards. Kindly include this jQuery.easing dependency for versions lesser than 14.3.0.49 in order to support animation effects.

Run the above code to render the following output.

![](Getting-Started_images/Getting-Started_img2.png) 

## Initialize the other widgets

To add the priority value to the **ListBox**, the text value is received from the input element and color for each priority is received by the **ColorPicker** control. To add each new priority value to the **ListBox** control click the **Add** button.

You can refer the following link for more information on creation of **ListBox**.
<http://help.syncfusion.com/js/listbox/overview>

The following code example is used to create the Priority form using **ListBox** control and **ColorPicker** control.

{% highlight html %}

   <div class="priorityWrapper">
   <div class="row">
            <div class="element-area">
                <div class="frameWrapper">
                    <div id="control">
                        <ul ej-listbox id="selectcheck">
                            <li><span class="color high"></span>High</li>
                            <li><span class="color normal"></span>Normal</li>
                            <li><span class="color low"></span>Low</li>
                        </ul>
                    </div>
                </div>
                <div id="Properties">
                    <table class="prop-grid">
                        <tr class="row">
                            <td class="column">Name
                            </td>
                            <td class="column">
                                <input type="text" id="categoryName" ng-model="textval"/>
                            </td>
                        </tr>
                        <tr class="row">
                            <td class="column">Color
                            </td>
                            <td class="column">
                                <!--Colorpicker element-->
                                <input id="CategoryColor" ej-colorpicker e-value="#278787" />
                            </td>
                            <td class="column">
                                <!--Add button for add the new category-->
                                <button class="e-btn e-select" id="AddCategory" ej-button e-text="Add" e-height="21px" e-width="82px"></button>
                                <input type="button" class="e-btn e-select" id="AddCategory" />
                            </td>
                        </tr>
                        <tr class="row"></tr>
                    </table>
                </div>
            </div>
   </div>
   </div>

{% endhighlight %}

Add the following in the script section.

{% highlight javascript %}

        angular.module('ColorPickCtrl', ['ejangular'])
           .controller('ColorPickCtrller', function ($scope) {
                    $scope.textval = "";
              }
           });

{% endhighlight %}

Add the following style section to align form fields. 

{% highlight css %}

<style>
    
    .row .element-area {
        height: 270px;
        width: 415px;
    }

    .priorityWrapper > .row {
        width: 415px;
        border: 1px solid #bbbcbb;
        padding: 16px;
        height: 275px;
        background-color: #fff;
    }

    .frameWrapper {
        float: left;
    }

    .color.high {
        background-color: red;
    }

    .color.normal {
        background-color: green;
    }

    .color.low {
        background-color: blue;
    }

    .element-area {
        width: 205px;
    }

    .element-area, #Properties {
        display: inline-block;
        float: left;
    }

    #Properties #categoryName {
        width: 140px;
        height: 20px;
    }

    #Properties .column {
        display: inline-block;
        width: 45px;
        margin: 10px 0 0;
    }

    #Properties .row {
        padding: 10px 0px 5px 0px;
    }

    #Properties {
        margin-left: 20px;
        width: 192px;
    }

    .color {
        width: 13px;
        height: 13px;
        border: 1px solid;
        display: inline-block;
        margin-right: 6px;
        margin-bottom: -3px;
    }
</style>

{% endhighlight %}

Run the above code to render the following output.

![](Getting-Started_images/Getting-Started_img3.png) 

## Add value with Selected Color 

You can add the value to **ListBox** with selected color by performing the button click event. The following script section defines the click event for the button element.

Initialize the click event for the button element in **&lt;script&gt;** tag.

{% highlight html %}

<ul ej-listbox id="selectcheck" e-create="onCreate">
    <li><span class="color high"></span>High</li>
    <li><span class="color normal"></span>Normal</li>
    <li><span class="color low"></span>Low</li>
</ul>
<input type="text" id="categoryName" ng-model="textval"/>
<button class="e-btn e-select" id="AddCategory" ej-button e-text="Add" e-height="21px" e-width="82px" e-click="addCategoryValue" ></button>

{% endhighlight %}

{% highlight javascript %}

        angular.module('ColorPickCtrl', ['ejangular'])
           .controller('ColorPickCtrller', function ($scope) {
                $scope.textval = "";
                $scope.onCreate = function(e) {
                    listBoxObj = $("#" + this._id).ejListBox('instance')
                }
                $scope.addCategoryValue = function(e) {
                    $scope.textval = "";
                    listBoxObj.addItem("<span class='color' style='background-color: " + colorObj.getValue() + "' ></span>" + $("#categoryName").val());
                }
              }
           });

{% endhighlight %}

{% highlight javascript %}

    jQuery(function ($) {
        //reuse the previous section script block
        //initliaze the button with click event
        $("#AddCategory").ejButton({ text: "Add", click: "addCategoryValue", width: "82px", height: "21px" });
    });

    //The following function used to add the new value to the listbox control
    function addCategoryValue() {
        if ($("#categoryName").val() !== "") {
            //To get the selected color from the colorpicker by using getValue()
            listBoxObj.addItem("<span class='color' style='background-color: " + colorObj.getValue() + "' ></span>" + $("#categoryName").val());
            $("#categoryName").val("");
        }
    }

{% endhighlight %}

The following screenshot illustrates the resultant output after you click **Add** button.

![](Getting-Started_images/Getting-Started_img4.png)  

