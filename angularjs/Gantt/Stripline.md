---
layout: post
title: Stripline
description: stripline
platform: AngularJS
control: Gantt
documentation: ug
---

# Stripline

The stripline in the Gantt control is used to highlight the important event in Gantt chart part. By using this feature, you can add the striplines to highlight important days in your project. The following code example shows how to add the stripline in Gantt control:

{% highlight javascript %}

<body ng-controller="GanttCtrl">
   <!--Add  Gantt control here-->    
   <div id="GanttContainer" ej-gantt
      //...
      e-striplines="stripLines" 
      >
   </div>
  <script>
    var stripLines= [{
            day: "01/02/2014",
            label: "Project Release",
            lineStyle: "dotted",
            lineColor: "Dark blue",
            lineWidth: 2
        }]
    angular.module('listCtrl', ['ejangular'])
        .controller('GanttCtrl', function($scope) {
            //...
            $scope.stripLines = "stripLines";
        });
</script>
</body>

{% endhighlight %}

The following screenshot shows the stripline in Gantt control:

![](Stripline_images/Stripline_img1.png)
