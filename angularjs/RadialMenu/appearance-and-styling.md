---
layout: post
title: Syncfusion Radial Menu Appearance and Styling 
description: appearance and styling
platform: AngularJS
control: RadialMenu
documentation: ug
---

# Appearance and Styling

You can customize RadialMenu component style and the appearance by using available themes or **e-cssClass** property.

## Theme

RadialMenu component style and appearance can be controlled based on CSS classes. In order to apply styles to the RadialMenu component, refer 2 files namely: ej.widgets.core.min.css and ej.theme.min.css. If the file ej.web.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.web.all.min.css is the combination of these two.

By default, there are 13the following themes support available for **RadialMenu** component namely

* flat-azure
* flat-azure-dark
* flat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark
* bootstrap-theme
* office-365
* material theme
* high contrast 01
* high contrast 02


## CSS Class

RadialMenu component’s appearance can only be customized using its CSS classes. Define CSS class, as per requirement and assign the class name to cssClass property.

### Configure RadialMenu using CSS class

Define e-cssClass to customize the RadialMenu.

In the HTML page, define the li items for RadialMenu component.

{% highlight html %}

    <ej-radialmenu id="radialmenu" e-targetelementid="radialtarget1" e-cssclass="customCss" >
    <e-items>
        <e-item e-imageurl="http://js.syncfusion.com/UG/web/Content/radial/copy.png" e-text="Copy"></e-item>
        <e-item e-imageurl="http://js.syncfusion.com/UG/web/Content/radial/paste.png" e-text="Paste"></e-item>
        <e-item e-imageurl="http://js.syncfusion.com/UG/web/Content/radial/redo.png" e-text="Redo"></e-item>
        <e-item e-imageurl="http://js.syncfusion.com/UG/web/Content/radial/undo.png" e-text="Undo"></e-item>
    </e-items>
    </ej-radialmenu>

{% endhighlight %}

Add the following styles in your code.

{% highlight css %}

    <style type="text/css">

        /* Customize the radialmenu */

       .e-radialmenu .e-default, .e-radialmenu .e-outerdefault.customCss 

       {

            fill:#f00;
       } 

    </style>

{% endhighlight %}

Output of RadialMenu configured based on CSS class is as follow,

![Appearance and Styling](apperance-and-styling-images\appearance-and-styling_img1.png)


