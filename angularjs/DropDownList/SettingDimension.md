---
layout: post
title: Demension in DropDownList widget
description: Setting Dimensions to DropDownList widget
platform: AngularJS
control: DropDownList
documentation: ug
keywords: Auto Sizing, DropDownList, dropdown, popup size, 
---

# Setting dimensions 

## Widget Sizing

### Fixed Size DropDownList widget

You can customize the widget dimensions using [width](http://help.syncfusion.com/api/js/ejdropdownlist#members:width) and [height](http://help.syncfusion.com/api/js/ejdropdownlist#members:height) properties. Fixed size values can be specified in pixel or percentage values. By default the DropDownList wrapper will be assigned with "143px" width and "30px" height.

### Fixed size popup list

You can customize the popup list dimensions using [popupWidth](http://help.syncfusion.com/api/js/ejdropdownlist#members:popupwidth) and [popupHeight](http://help.syncfusion.com/api/js/ejdropdownlist#members:popupheight) properties. Fixed size values can be specified in pixel or percentage values. By default popup width is auto and popup height is "152px". 

### Auto Sizing

DropDownList is adaptive to mobile and web layout such that it is adjustable with screen resolution. The textbox will be rendered based on its parent containers dimensions on assigning 100% values to the width property. Default value for popupWidth is auto, so when you assign 100% to popupWidth then it will be rendered based on specified range.

### Limit the number of items

You can use [itemsCount](http://help.syncfusion.com/api/js/ejdropdownlist#members:itemscount) property to fetch only the specific number of items from the data source. To fetch the remaining items you can enable [virtual scrolling](databinding#virtual-scrolling) support which loads the data on scrolling the data items in popup list. 

N> By default popup list is shown on DropDownList button click but you can display the list initially by enabling the [showPopupOnLoad](http://help.syncfusion.com/api/js/ejdropdownlist#members:showpopuponload) property. You can also use [showPopup ()](http://help.syncfusion.com/api/js/ejdropdownlist#methods:showpopup) or [hidePopup ()](http://help.syncfusion.com/api/js/ejdropdownlist#methods:hidepopup) methods at run time to display or hide the popup list.

{% highlight html %}

    <input type="text" id="selectcompany" ej-dropdownlist e-datasource="data" e-fields-text="text" e-fields-value="value" e-itemscount="3" e-showpopuponload="true">
     
{% endhighlight %}

{% highlight javascript %}

        var items = [{
            text: "ListItem 1",
            value: "item1"
        }, {
            text: "ListItem 2",
            value: "item2"
        }, {
            text: "ListItem 3",
            value: "item3"
        }, {
            text: "ListItem 4",
            value: "item4"
        }, {
            text: "ListItem 5",
            value: "item5"
        }];

        angular.module('dropdownlistApp', ['ejangular'])
        .controller('dropdownlistCtrl', function ($scope) {
            $scope.data = items;
        });

{% endhighlight %}

![](SettingDimension_images/SettingDimension_img1.png)

## Popup resizing 

To show a resize handle in the popup list, use [enablePopupResize](http://help.syncfusion.com/api/js/ejdropdownlist#members:enablepopupresize) property. You can customize the resize functionality by setting dimensions to the following properties.

<table>
    <tr>
        <td>
            {{'[minPopupWidth](http://help.syncfusion.com/api/js/ejdropdownlist#members:minpopupwidth)'| markdownify }}
            <br/>
        </td>
        <td>
            Default value is 0, once set you cannot resize below to the specified width
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            {{'[maxPopupWidth](http://help.syncfusion.com/api/js/ejdropdownlist#members:maxpopupwidth)'| markdownify }}
            <br/>
        </td>
        <td>
            Default value is null, once set you cannot extend beyond to the specified width
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            {{'[minPopupHeight](http://help.syncfusion.com/api/js/ejdropdownlist#members:minpopupheight)'| markdownify }}
            <br/>
        </td>
        <td>
            Default value is 0, once set you cannot resize below to the specified height
            <br/>
        </td>
    </tr>
    <tr>
        <td>
            {{'[maxPopupHeight](http://help.syncfusion.com/api/js/ejdropdownlist#members:maxpopupheight)'| markdownify }}
            <br/>
        </td>
        <td>
            Default value is null, once set you cannot extend beyond to the specified height
            <br/>
        </td>
    </tr>
</table>

{% highlight html %}

    <input type="text" id="selectcompany" ej-dropdownlist e-datasource="data" e-fields-text="text" e-fields-value="value" e-enablepopupresize="true" e-minpopupwidth="150" e-minpopupheight="150" e-maxpopupwidth="550" e-maxpopupheight="550">
    
{% endhighlight %}

{% highlight javascript %}
	
        var items = [{
            text: "ListItem 1",
            value: "item1"
        }, {
            text: "ListItem 2",
            value: "item2"
        }, {
            text: "ListItem 3",
            value: "item3"
        }, {
            text: "ListItem 4",
            value: "item4"
        }, {
            text: "ListItem 5",
            value: "item5"
        }];

        angular.module('dropdownlistApp', ['ejangular'])
        .controller('dropdownlistCtrl', function ($scope) {
            $scope.data = items;
        });

{% endhighlight %}

![](SettingDimension_images/SettingDimension_img2.png)

![](SettingDimension_images/SettingDimension_img3.png)