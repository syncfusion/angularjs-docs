---
layout: post
title: Drill-Down-Support
description: drill down support
platform: AngularJS
control: TreeMap
documentation: ug
---

# Drill Down Support

**Treemap** enables drill down to expose the hierarchy achieved by clicking on a node and this results in enabling the **Treemap** to move to the next level or sub level and can return back to the normal **Treemap** view by clicking on the node header. Only a single level of the **Treemap** is visible at once.

## Enable Drill Down

**Treemap** elements can be drilled down by setting the `e-enableDrillDown` property to true. You can view the hierarchy of the **Treemap** by clicking on the treemap items and can move to the previous level by clicking on the drill down header. The header color can be customized by changing the values in the property `e-drillDownHeaderColor` and the selection color can be done by changing the `e-drillDownSelectionColor` property.

<table>
<tr>
<th>
Property</th><th>
Type</th><th>
Description</th></tr>
<tr>
<td>
enableDrillDown</td><td>
bool</td><td>
Gets or sets a value that indicates whether the drill down feature is enabled or not</td></tr>
<tr>
<td>
drillDownHeaderColor</td><td>
string</td><td>
Gets or sets a color for header during drill down</td></tr>
<tr>
<td>
drillDownSelectionColor</td><td>
string</td><td>
Gets or sets a color for highlighting tree map item during drill down.</td></tr>
</table>


{% highlight html %}

   <html xmlns="http://www.w3.org/1999/xhtml" lang="en" ng-app="TreemapApp">
    <head>
        <title>Essential Studio for AngularJS: TreeMap</title>
        <!--CSS and Script file References -->
    </head> 
    <body ng-controller="TreemapCtrl">
     <div id="mapContainer" style="align-content:center;width: 800px; height: 400px;">
     <ej-treemap e-datasource=populationdata e-enabledrilldown="true" e-drilldownheadercolor="#199DAF" 
     e-drilldownselectioncolor="#199DAF" e-unicolormapping-color="#CCDFE3" 
     e-weightvaluepath="Population">
     <e-levels>
     <e-level e-grouppath="Continent" e-showlabels="true" e-headerheight="25" e-showheader="true" e-headertemplate="headertemplate" 
     e-groupgap="5"></e-level>
     <e-level e-grouppath="Country" e-showlabels="true" e-headerheight="25" e-showheader="true" e-headertemplate="headertemplate" 
     e-groupgap="0"></e-level>
     <e-level e-grouppath="Name" e-showlabels="true" e-headerheight="25" e-showheader="true" e-headertemplate="headertemplate" 
     e-groupgap="0"></e-level>
     </e-levels>
     </ej-treemap>
     </div>
     <script>
     angular.module('TreemapApp', ['ejangular'])
     .controller('TreemapCtrl', function ($scope) {
                        });
    </script>
    </body>
</html> 
    
    {% endhighlight %}



![](Drill-Down-Support_images/Drill-Down-Support_img1.png)

_Before Drill Down_

![](Drill-Down-Support_images/Drill-Down-Support_img2.png)

_After Drill Down_

