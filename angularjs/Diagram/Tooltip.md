---
layout: post
title: Show tooltips when mouse hovers over objects
description: How to show/hide tooltips when mouse hovers over objects or during interaction?
platform: AngularJS
control: Diagram
documentation: ug
---

# Tooltip
In Graphical User Interface (GUI), tooltip is a message that is displayed when mouse hovers over an element. Diagram provides tooltip support while dragging, resizing, rotating a node, and when mouse hovers any Diagram element.

## Default tooltip

By default, Diagram displays a tooltip to provide the size, position, and angle related information while dragging, resizing, and rotation. The following images illustrate how the Diagram displays the node information during interaction.

| Drag | Resize | Rotate |
|---|---|---|
| ![](/angularjs/Diagram/Tooltip_images/Tooltip_img1.png) | ![](/angularjs/Diagram/Tooltip_images/Tooltip_img2.png) | ![](/angularjs/Diagram/Tooltip_images/Tooltip_img3.png) |

### Disable default tooltip

To disable the default tooltip, You need to set `selectedItems.tooltip` as `null`. The following code example illustrates how to disable default tooltip.

{% highlight html %}

<div ng-controller="diagramCtrl">
    <ej-diagram id="diagram" e-height="500px" e-width="100%" e-selectedItems="selectedItems">
    </ej-diagram>
</div>

{% endhighlight %} 

{% highlight javascript %}

syncApp.controller('diagramCtrl', function($scope) {
    //Disable tooltip during interaction
    $scope.selectedItems = {
        tooltip: null
    }
});

{% endhighlight %} 

## Common tooltip for all nodes and connectors

Diagram provides support to show tooltip when mouse hovers over any node/connector. 
To show tooltip on mouse over, the `tooltip` property of Diagram model needs to be set with the tooltip `templateId` and `alignment` as shown in the following example.

{% highlight html %}

<div ng-controller="diagramCtrl">
    <ej-diagram id="diagram" e-height="500px" e-width="100%" e-nodes="nodes" e-tooltip-templateid="tooltip.templateId" 
	 e-tooltip-alignment-horizontal="tooltip.alignment.horizontal" e-tooltip-alignment-vertical="tooltip.alignment.vertical">
    </ej-diagram>
</div>

<!--Define tooltip template-->
<script type="text/x-jsrender" id="mouseovertooltip">
    <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;"> "{{:Designation}}"</span>
    </div>
</script>

{% endhighlight %}

{% highlight javascript %}

var nodes = [{
    name: "elizabeth",
    width: 70,
    height: 40,
    offsetX: 100,
    offsetY: 100,
    fillColor: "darkCyan",
    labels: [{
        text: "Elizabeth",
        fontColor: "white",
        bold: "true"
    }],
    Designation: "Managing Director"
}]

syncApp.controller('diagramCtrl', function($scope) {
    //Defines mouse over tooltip
    $scope.nodes = nodes;
    $scope.tooltip = {
        templateId: "mouseovertoolTipId",
        alignment: {
            horizontal: "center",
            vertical: "bottom"
        },
    };
});

{% endhighlight %} 

![](/angularjs/Diagram/Tooltip_images/Tooltip_img4.png)

### Disable tooltip at runtime

Tooltips on mouse over can be disabled by assigning `tooltip` property as `null`. The following code example illustrates how to disable the mouse over tooltip at runtime.

{% highlight javascript %}

 syncApp.controller('diagramCtrl', function($scope) {
     //Defines mouse over tooltip
     $scope.tooltip = null;
 });

{% endhighlight %} 

## Tooltip for a specific node/connector

Tooltips can be customized for every node. Tooltip can be defined for individual node/connector by using the `tooltip` property of that node/connector. In addition to that, you have to remove the **InheritTooltip** option from the `constraints` of that node/connector. The following code example illustrates how to customize tooltips for individual elements.

{% highlight javascript %}

var NodeConstraints = ej.datavisualization.Diagram.NodeConstraints;

//Customizes tooltip for a node/connector
var node = {
    //Remove InheritTooltip not to inherit the tooltip defined in model
    constraints: NodeConstraints.Default & ~NodeConstraints.InheritTooltip,
    //Defines mouse over tooltip for a node
    tooltip: {
        templateId: "nodetooltiptemplate"
    }
};

//Disables tooltip for any node/connector
node = {
    //Removes InheritTooltip not to inherit the tooltip defined in model
    constraints: NodeConstraints.Default & ~NodeConstraints.InheritTooltip,
    //Disables tooltip for a node
    tooltip: null
};

{% endhighlight %} 

## Tooltip alignments

### Tooltip relative to object

Diagram provides support to show tooltip around the node/connector that is hovered by mouse. You can align the tooltip as you wish by using the `alignment` and `margin` properties of tooltip. The `relativeMode` property of tooltip defines whether the tooltip has to be displayed around the object or at the mouse position. The following code example illustrates how to position the tooltip around object.

{% highlight html %}

<!--Define tooltip template-->
<script type="text/x-jsrender" id="mouseovertooltip">
    <div style="background-color: #F08080; color: white; padding: 5px;">
        <span> "{{:Designation}}" </span>
    </div>
</script>

{% endhighlight %}

{% highlight javascript %}

var NodeConstraints = ej.datavisualization.Diagram.NodeConstraints;

var nodes = {
    name: "elizabeth",
    width: 70,
    height: 40,
    offsetX: 100,
    offsetY: 100,
    //Removes inherit tooltip from constraints
    constraints: NodeConstraints.Default & ~NodeConstraints.InheritTooltip,
    //Defines tooltip
    tooltip: {
        //Defines template id
        templateId: "mouseovertooltip",
        //Sets to show tooltip around the element
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Object,
        //Sets the alignment properties
        alignment: {
            //Defines horizontal alignment around node
            horizontal: "center",
            //Defines vertical alignment around node
            vertical: "top"
        }
    },
    Designation: "Director",
    fillColor: "darkcyan",
    labels: [{
        text: "Elizabeth",
        fontColor: "white"
    }]
};

{% endhighlight %}

![](/angularjs/Diagram/Tooltip_images/Tooltip_img5.png)

### Tooltip relative to mouse position

To display the tooltip at mouse position, you need to set "mouse" option to the `relativeMode` property of tooltip. The following code example illustrates how to show tooltip at mouse position.

{% highlight javascript %}

var NodeConstraints = ej.datavisualization.Diagram.NodeConstraints;

//Defines tooltip template as mentioned in the previous snippet
var nodes = {
    name: "elizabeth",
    width: 70,
    height: 40,
    offsetX: 100,
    offsetY: 100,
    //Removes inherit tooltip from constraints
    constraints: NodeConstraints.Default & ~NodeConstraints.InheritTooltip,
    //Defines tooltip
    tooltip: {
        //Sets to show tooltip at mouse position
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Mouse,
        //Defines template id
        templateId: "mouseovertooltip",
        //Sets margin - absolute distance between mouse position and tooltip
        margin: {
            top: 10,
            left: 10
        },
    },
    Designation: "Director",
    fillColor: "darkcyan",
    labels: [{
        text: "Elizabeth",
        fontColor: "white"
    }]
};

{% endhighlight %}

![](/angularjs/Diagram/Tooltip_images/Tooltip_img6.png)


