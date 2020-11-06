---
layout: post
title: Syncfusion Radial Slider appearance and styling
description: appearance and styling
platform: AngularJS
control: Radial Slider
documentation: ug
---

## Appearance and Styling

### Theme

You can customize RadialSlider component style and the appearance by using available themes or cssClass property.

In order to apply styles to the RadialSlider component, refer to 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. When you refer ej.web.all.min.css file, it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.web.all.min.css is the combination of these two.

By default, there are 17 theme support available for RadialSlider component, namely:

* flat-azure

* flat-azure-dark

* fat-lime

* flat-lime-dark

* flat-saffron

* flat-saffron-dark

* gradient-azure

* gradient-azure-dark

* gradient-lime

* gradient-lime-dark

* gradient-saffron

* gradient-saffron-dark

* bootstrap

* material

* high-contrast-01

* high-contrast-02

* office-365

### CSS Class

**RadialSlider** component also allows you to customize its appearance using user-defined CSS. To apply custom themes you can use **e-cssClass** property, which sets the root class for **RadialSlider** theme.

Using this **e-cssClass** you can override the existing styles under the theme style sheet. In the following example, the value of **cssClass** property is set as “**Purple-dark**”. **Purple-dark** is added as root class to **RadialSlider** component at the runtime. From this root class, you can customize the **RadialSlider** appearance.

Add the following code in your **HTML** page to render the RadialSlider.

{% highlight html %}


<div id="angularRadialSlider" ej-radialslider e-cssClass="cssClass" e-innercircleimageurl="http://js.syncfusion.com/demos/web/content/images/radialslider/chevron-right.png"></div>


{% endhighlight %}


{% highlight js %}

syncApp.controller('radialSliderCtrl', function ($scope) {
        $scope.cssClass = “purple-dark”;
    });


{% endhighlight %}


In the following style sheet the exiting theme style sheet file has been over-ridden using root class “**Purple-dark**”.

Add the following code in your style section.

{% highlight css %}


.Purple-dark{ background-color:pink; }


{% endhighlight %}


The following screenshot illustrates the output of the above code.

![Appearance and Styling](Appearance-and-Styling_images\cssclass_img1.png)


