---
layout: post
title: Color-Mapping
description: color mapping
platform: AngularJS
control: pivottreemap
documentation: ug
keywords: ejpivottreemap, pivottreemap, pivottreemap widget, js pivottreemap 
---

# Color Mapping

You can customize the colors of the leaf nodes of PivotTreeMap using the color mapping support. 

Color mapping is categorized into two different types such as,

* Normal
* Range

You can color all the leaf nodes with the different colors by setting the `color` value of the `rangeColorMapping` property.

### Normal Color Mapping

You can customize the nodes based on number of leaf items using different color ranges. You can also define the color value range using `from` and `to` properties.

The following code sample explains how to customize PivotTreeMap appearance using **Normal** mode (i.e., differentiate color based on number of the leaf items in each header).

{% highlight html %}

<body>
    <div ng-controller="PivotTreeMapCtrl">
        <div id="PivotTreeMap1" ej-pivottreemap e-dataSource="dataSource" e-renderSuccess= "onTypeChange"></div>
        <!--Tooltip labels can be localized here-->
        <script id="tooltipTemplate" type="application/jsrender">
            <div style="background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;">
                <div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
            </div>
        </script>   
    </div>
    <script>
        angular.module('PivotTreeMapApp', ['ejangular']).controller('PivotTreeMapCtrl', function ($scope) {
            $scope.dataSource = {
                data: "http://bi.syncfusion.com/olap/msmdpump.dll;Locale identifier=1033;", //data
                catalog: "Adventure Works DW 2008 SE",
                cube: "Adventure Works",
                ///...
            };
            $scope.onTypeChange = function(args){
				treemapTarget = $('#PivotTreeMap1TreeMapContainer').data("ejTreeMap");
				treemapTarget.model.colorValuePath = "";
				treemapTarget.model.enableGradient = false;
				treemapTarget.model.showLegend = false;
				treemapTarget.model.legendSettings.leftLabel = "";
				treemapTarget.model.legendSettings.rightLabel = "";
				treemapTarget.model.rangeColorMapping = [];
				treemapTarget.model.colorValuePath = "Index";
				treemapTarget.model.rangeColorMapping.push(
				{ color: "#9de24f", from: "0", to: "0" },
                { color: "#a2e2fe", from: "1", to: "1" },
                { color: "#ffff66", from: "2", to: "2" },
                { color: "#FF0040", from: "3", to: "3" },
                { color: "#f6b53f", from: "4", to: "4" },
                { color: "#6FAAB0", from: "5", to: "5" },
                { color: "#C4C24A", from: "6", to: "6" }
                )
				treemapTarget.refresh();
			  }
        });
    </script>
</body>

{% endhighlight %}

![](Color-Mapping_images/ColorMapping_img1.png)

### Range Color Mapping

You can customize the nodes based on its value and color ranges using **Range** color. You can also define the color value range using `from` and `to` properties.

The following code sample explains how to customize PivotTreeMap appearance using **Range** mode (i.e., differentiate color for leaf items based on values).

{% highlight html %}

<script>
    angular.module('PivotTreeMapApp', ['ejangular']).controller('PivotTreeMapCtrl', function ($scope) {
        $scope.dataSource = {
            data: "http://bi.syncfusion.com/olap/msmdpump.dll;Locale identifier=1033;", //data
            catalog: "Adventure Works DW 2008 SE",
            cube: "Adventure Works",
            ///...
        };
        $scope.onTypeChange = function(args){
            treemapTarget = $('#PivotTreeMap1TreeMapContainer').data("ejTreeMap");
            treemapTarget.model.colorValuePath = "";
            treemapTarget.model.enableGradient = false;
            treemapTarget.model.showLegend = false;
            treemapTarget.model.legendSettings.leftLabel = "";
            treemapTarget.model.legendSettings.rightLabel = "";
            treemapTarget.model.rangeColorMapping = [];
            treemapTarget.model.colorValuePath = "Value";
            treemapTarget.model.rangeColorMapping.push(
            { color: "#a2e2fe", from: "0", to: "10" },
            { color: "#9de24f", from: "11", to: "250" },
            { color: "#ffff66", from: "251", to: "1000" },
            { color: "#C4C24A", from: "1001", to: "3000" },
            { color: "#f6b53f", from: "3001", to: "5000" },
            { color: "#6FAAB0", from: "5001", to: "10000" },
            { color: "#FF0040", from: "10001", to: "20000" }
            )
            treemapTarget.refresh();
            }
    });
</script>

{% endhighlight %}

![](Color-Mapping_images/ColorMapping_img2.png)



