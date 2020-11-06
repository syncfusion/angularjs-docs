---
layout: post
title: signature customization
description: signature customization
platform: AngularJS
control: Signature
documentation: ug
---

## Signature Customization

### Background color

Signature component allows you to set the background color for the component using the **e-backgroundcolor** property. When we set our required background, then the signature’s background color will be changed automatically.

The following code example is used to render the Signature component with background color

Add the following HTML and script to render signature with customized background color.

{% highlight html %}


<div id="signature" ej-signature e-height="height" e-width="width" e-isresponsive="true" e-strokecolor="strokecolor" e-backgroundcolor="backgroundColor"></div>     


{% endhighlight %}


{% highlight js %}

syncApp.controller('signatureCtrl', function ($scope) {
             $scope.height = 300,
             $scope.width = 600,
             $scope.strokecolor = "red",
             $scope.backgroundColor = "grey"

        });

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined background color.

![https://help.syncfusion.com/js/signature/Signature_Customization_images/backgroundcolor_img1.png](Signature_Customization_images\backgroundcolor_img1.png)


### Background Image

Signature component allows you to set the background image for the component using the **e-backgroundimage** property. When we set our required background image, then the signature’s canvas will be changed with the given image.

The following code example is used to render the Signature component with customized background image.

Add the following HTML and script to render signature with custom defined background image.

{% highlight html %}

<div id="signature" ej-signature e-height="height" e-width="width" e-isresponsive="true" e-backgroundimage="backgroundImage"></div>     

{% endhighlight %}


{% highlight js %}

syncApp.controller('signatureCtrl', function ($scope) {
           $scope.height = 300,
           $scope.width = 600,
           $scope.backgroundImage ="http://js.syncfusion.com/UG/Mobile/Content/sports.png"

        });

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined background image.

![](backgroundimage_images\backgroundimage_img1.png)

### Stroke color

Signature component allows you to set the stroke color for the signature stroke using the **e-strokecolor** property. When we set our required color, then the signature’s stroke color will be changed.

The following code example is used to render the Signature component with stroke color.

Add the following script to render signature with customized stroke color.

{% highlight html %}

<div ng-controller="signatureCtrl">
        <div id="signature" ej-signature e-height="height" e-width="width" e-isresponsive="true" e-strokecolor="strokecolor"></div>     
    </div>

{% endhighlight %}


{% highlight js %}

    syncApp.controller('signatureCtrl', function ($scope) {
             $scope.height = 300,
             $scope.width = 600,
             $scope.strokecolor = "red"

        });


{% endhighlight %}


The following screenshot illustrates the Signature with custom defined stroke color.

![https://help.syncfusion.com/js/signature/Signature_Customization_images/strokecolor_img1.png](Signature_Customization_images\strokecolor_img1.png)

### Stroke Width

Signature component allows you to set the stroke width for the component using the **e-strokewidth** property. When we set our required width, then the signature’s stroke width will be changed.

The following code example is used to render the Signature component with maximum stroke value.

Add the following HTML and script to render signature with customized stroke width.

{% highlight html %}


<div ng-controller="signatureCtrl">
        <div id="signature" ej-signature e-height="height" e-width="width" e-isresponsive="true" e-strokewidth="strokewidth"></div> 
</div>


{% endhighlight %}


{% highlight js %}

       syncApp.controller('signatureCtrl', function ($scope) {
             $scope.height = 300,
             $scope.width = 600,
             $scope.strokewidth = 5

        });

{% endhighlight %}

The following screenshot illustrates the Signature with custom defined stroke maximum value.

![https://help.syncfusion.com/js/signature/Signature_Customization_images/strokewidth_img1.png](Signature_Customization_images\strokewidth_img1.png)
