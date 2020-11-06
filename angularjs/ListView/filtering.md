---
layout: post
title: filtering
description: filtering
platform: AngularJS
control: ListView
documentation: ug
---

## Filtering

**Filtering** is one of the key features of **ListView** component. The **Filtering** option is added into the **ListView** component when the **e-enablefiltering** property is set to **“True”**. This enables a simple interface to filter items from a large collection of **ListView** items.

Refer the following code examples.

{% highlight html %}


  <div ej-listview id="anglistview" e-width="width" e-enablefiltering="enableFilter">
                    <ul>
                        <li data-ej-text="Artwork"></li>
                        <li data-ej-text="Abstract"></li>
                        <li data-ej-text="2 Acrylic Mediums"></li>
                        <li data-ej-text="Creative Acrylic"></li>
                        <li data-ej-text="Modern Painting"></li>
                        <li data-ej-text="Canvas Art"></li>
                        <li data-ej-text="Black white"></li>
                        <li data-ej-text="Children"></li>
                        <li data-ej-text="Preschool Crafts"></li>
                        <li data-ej-text="School-age Crafts"></li>
                    </ul>
                </div>


{% endhighlight %}





Add the following script in your code.

{% highlight js %}


syncApp.controller('ListViewCtrl', function ($scope) {
    $scope.width = 400; 
    $scope.enableFilter = true;
});



{% endhighlight %}



**Screenshot:**

![https://help.syncfusion.com/js/ListView/Filtering_images/Filtering_img1.png](filtering_images\filtering_img1.png)

_Before Filtering_

![https://help.syncfusion.com/js/ListView/Filtering_images/Filtering_img2.png](filtering_images\filtering_img2.png)

_After Filtering_

