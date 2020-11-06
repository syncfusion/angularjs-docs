---
layout: post
title: Represent the data to render the Diagram control
description: How to represent the data to render the Diagram control?
platform: AngularJS
control: Diagram
documentation: ug
---

# Model

The Diagram model represents the data to render the Diagram and to manipulate the Diagram elements. The following code illustrates how to define Diagram model.

{% highlight html %}

//Creates diagram

<div ng-controller="diagramCtrl">
    <div>
        <ej-diagram id="diagram" e-width="100%" e-height="600px" e-pagesettings-pageWidth="pageSettings.pageWidth" 
        e-pagesettings-pageHeight="pageSettings.pageHeight">
        </ej-diagram>
    </div>
</div>

{% endhighlight %}

{% highlight javascript %}

    syncApp.controller('diagramCtrl', function($scope) {
      $scope.pageSettings = {
          pageWidth: 2000,
          pageHeight: 2000,
      };
  });

{% endhighlight %}

![](/angularjs/Diagram/Model_images/Model_img1.png)
