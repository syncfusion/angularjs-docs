---
layout: post
title: Syncfusion Rotator data fields and configuration
description: data fields and configuration
platform: AngularJS
control: rotator
documentation: ug
---

## Data fields and Configuration

The following sub-properties provide a way to bind the data either locally/remotely to the Rotator control. The value set to this property is object type.

### DataSource

This property specifies the list of data that contains a set of data fields. Each data value is used to render an item for the Rotator. The value set to this property is object type.

### Fields

It defines mapping fields for the data items of the Rotator. The value set to this property is object type.

<table>
<tr>
<td>
Name</td><td>
Description</td></tr>
<tr>
<td>
text</td><td>
It specifies the text content of the tag. The value set to this property is string type.</td></tr>
<tr>
<td>
url</td><td>
This property specifies the URL for an image. The value set to this property is string type.</td></tr>
<tr>
<td>
linkAttribute</td><td>
This property specifies a link for the image. The value set to this property is string type.</td></tr>
<tr>
<td>
targetAttribute</td><td>
This property specifies where to open a given link. The value set to this property is string type.</td></tr>
<tr>
<td>
thumbnailText</td><td>
This property specifies a caption for the thumbNailText. The value set to this property is string type.</td></tr>
<tr>
<td>
thumbnailUrl</td><td>
This property specifies the URL for the thumbnail image. The value set to this property is string type.</td></tr>
</table>


### Query

This property retrieves data from remote data. This property is applicable only when a remote data source is used. Each data value is used to render an item for the Rotator. The value set to this property is object type.

### Local data binding

Rotator provides the data binding support for the Rotator item. So you can bind the data from JSON Data. For this behavior, you need to map the corresponding filed with their column names. The data can be bound as a list and it is assigned to e-dataSource property. You can refer the following code example to bind local data.

{% highlight html %}


   <ul id="sliderContent" ej-rotator e-datasource="dataList" e-slidewidth="600px" e-slideheight="350px" e-showpager="true" e-showcaption="true" e-showplaybutton="true" e-isresponsive="true" />

  <script>
         var list = [
{ text: "Green", url: " http://js.syncfusion.com/demos/web/content/images/rotator/green.jpg" },
{ text: "Snowfall", url: " http://js.syncfusion.com/demos/web/content/images/rotator/snowfall.jpg" },
{ text: "Beautiful Bird", url: " http://js.syncfusion.com/demos/web/content/images/rotator/bird.jpg" },
          { text: "Tablet", url: " http://js.syncfusion.com/demos/web/content/images/rotator/tablet.jpg" },
          { text: "Nature", url: " http://js.syncfusion.com/demos/web/content/images/rotator/nature.jpg" }];

        angular.module('rotateApp', ['ejangular']).controller('RotateCtrl', function ($scope) {
            $scope.dataList = list
        });
    </script>


{% endhighlight %}



![Data fields and Configuration](data fields and configuration_images\localdatabinding_img1.png)

