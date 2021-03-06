---
layout: post
title: Named Set
description: named set
platform: AngularJS
control: pivottreemap
documentation: ug
keywords: ejpivottreemap, pivottreemap, pivottreemap widget, js pivottreemap 
---

# Named Sets

Named Sets is a multidimensional expression (MDX) that returns a set of dimension members, which can be created by combining cube data, arithmetic operators, numbers and functions.

## Client Mode

You can bind the Named Sets in PivotTreeMap by setting it's unique name in the `fieldName` property either in row or column axis and `isNamedSets` boolean property to "true".

{% highlight html %}

<body>
    <div ng-controller="PivotTreeMapCtrl">
        <div id="PivotTreeMap1" ej-pivottreemap e-dataSource="dataSource"></div>
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
               data: "http://bi.syncfusion.com/olap/msmdpump.dll", //data 
               catalog: "Adventure Works DW 2008 SE", 
               cube: "Adventure Works", 
               columns: [{ 
                      fieldName: "[Customer].[Customer Geography]" 
               }], 
               rows: [{ 
                   fieldName: "[Core Product Group]", 
                   isNamedSets: true 
              }], 
              values: [{ 
                  measures: [{ 
                      fieldName: "[Measures].[Internet Sales Amount]", 
                 }], 
                 axis: "columns" 
              }] 
            };
        });
    </script>
</body>

{% endhighlight %}

![](NamedSets_images/namedset.png)


## Server Mode

You can add Named Sets in the PivotTreeMap by using `NamedSetElement` class in the OlapReport.

{% highlight C# %}

OlapReport olapReport = new OlapReport(); 
olapReport.Name = "Customer Report"; 
olapReport.CurrentCubeName = "Adventure Works"; 

DimensionElement dimensionElementColumn = new DimensionElement(); 
dimensionElementColumn.Name = "Customer"; 
dimensionElementColumn.AddLevel("Customer Geography", "Country ");
 
MeasureElements measureElementColumn = new MeasureElements(); 
measureElementColumn.Elements.Add(new MeasureElement { 
Name = "Internet Sales Amount" 
}); 

NamedSetElement dimensionElementRow = new NamedSetElement(); 
dimensionElementRow.Name = "Core Product Group"; 

olapReport.CategoricalElements.Add(dimensionElementColumn); 
olapReport.CategoricalElements.Add(measureElementColumn); 
olapReport.SeriesElements.Add(dimensionElementRow);

{% endhighlight %}

![](NamedSets_images/servernamedset.png)


