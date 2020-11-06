---
layout: post
title: Accordion-Panel-enabler
description: accordion panel enabler
platform: AngularJS
control: Accordion 
documentation: ug
keywords: ejaccordion, accordion, angularjs accordion
---

# Accordion Panel Enabler

## Enable/Disable widget

**You can enable or disable the Accordion** widget on initial rendering using the [enabled](https://help.syncfusion.com/api/js/ejaccordion#members:enabled) property. By default **enabled** property is set to true and the **Accordion** panels are active always. 

 The following steps explain that how to disable the **Accordion** widget

In an HTML page, define a &lt;div&gt; element that is a container for Accordion widget and add the contents correspondingly

{% highlight html %}
  
<div id="accordion" style="width: 500px" ej-accordion e-enabled="false">
    <h3>
        <a href="#">Orubase</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Orubase is the only mobile application development framework built especially for developing complex line-of-business mobile applications targeting iOS, Android, and Windows Phone platforms in the shortest possible timeframe.
    </div>
    <h3>
        <a href="#">WinRTXAML</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Essential Studio for WinRT contains all the controls you need to build line-of-business tablet applications including grid, chart, map, tree map, SSRS report viewer, rich-text editor, pdf viewer, gauges, barcode, editors, and much more. It also includes a unique set of controls for reading and writing Excel, Word, and PDF documents in Windows store apps.
    </div>
    <h3>
        <a href="#">Metro Studio</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Syncfusion Metro Studio is a collection of over 2500 Metro-style icon templates that can be easily customized to create thousands of unique Metro icons.
    </div>
</div>

{% endhighlight %}

Output for disabled Accordion control is as follows.


![](Accordion-Panel-enabler_images/Accordion-Panel-enabler_img1.png) 

## Enable panel items

You can enable the **Accordion** widget items on initial loading using [enabledItems](https://help.syncfusion.com/api/js/ejaccordion#members:enableditems) property. This property takes array of indices whose panel needs to be enabled in **Accordion** widget. 

The **disabledItems** property disables the **Accordion** items based on the index. This takes array of indices whose panel is to be disabled. 

### Enabling accordion panel items

The following steps explains you on how to enable the panel items in **Accordion** widget

In an HTML page, define a &lt;div&gt; element that is a container for Accordion widget and add the contents correspondingly.

{% highlight html %}
   
<div id="accordion" style="width: 500px" ej-accordion e-enablemultipleopen="true" e-enableditems="enableditem" e-disableditems="diableditems" e-selecteditemindex="1">
    <h3>
        <a href="#">Orubase</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Orubase is the only mobile application development framework built especially for developing complex line-of-business mobile applications targeting iOS, Android, and Windows Phone platforms in the shortest possible timeframe.
    </div>
    <h3>
        <a href="#">WinRTXAML</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Essential Studio for WinRT contains all the controls you need to build line-of-business tablet applications including grid, chart, map, tree map, SSRS report viewer, rich-text editor, pdf viewer, gauges, barcode, editors, and much more. It also includes a unique set of controls for reading and writing Excel, Word, and PDF documents in Windows store apps.
    </div>
    <h3>
        <a href="#">Metro Studio</a>
    </h3>
    <div>
        <!-- add accordion contents here to load contents under this header -->
        Syncfusion Metro Studio is a collection of over 2500 Metro-style icon templates that can be easily customized to create thousands of unique Metro icons.
    </div>
</div>

{% endhighlight %}


{% highlight javascript %}

  angular.module('AccordionApp', ['ejangular'])
    .controller('AccordionCtrl', function ($scope) {
        $scope.enableditems = [1, 2];
        $scope.diableditems = [0];
  });

{% endhighlight %}

Output for Accordion control with some enabled and disabled items, where first panel is disabled and it can’t be expanded or collapsed is as follows.


![](Accordion-Panel-enabler_images/Accordion-Panel-enabler_img2.png)