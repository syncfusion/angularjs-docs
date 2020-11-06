---
layout: post
title: Scrolling with Spreadsheet widget for Syncfusion Essential JS
description: How to enable Scrolling and its functionalities
platform: AngularJS
control: Spreadsheet
documentation: ug
--- 

# Scrolling

Scrolling helps you to move quickly to different areas of worksheet. Scrolling can be enabled by setting `allowscrolling` as true in `e-scrollsettings`. 

You can scroll through worksheet using one of the following ways,

* Using the arrow keys
* Using the scroll bars
* Using the mouse

## Set height and width for Scrolling

To set height and width in spreadsheet use `height` and `width` property in `e-scrollsettings`. The default value for `height` and `width` is `100%`. The height and width can be set in percentage and pixel. 

The following code example describes the above behavior.

{% highlight html %}
<body ng-controller="SpreadsheetCtrl">
     <div id="Spreadsheet" ej-spreadsheet e-scrollsettings-allowscrolling="true" e-scrollsettings-height="400" e-scrollsettings-width="50%"></div>
</body> 
{% endhighlight %}

{% highlight javascript %}
var syncApp = angular.module("defaultApp", ["ngRoute", "ejangular"]);
    syncApp.controller('SpreadsheetCtrl', function ($scope, $rootScope) {
    });
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](Scrolling_images/Scrolling_img1.png)

## Responsive

Spreadsheet has support for responsive behavior based on client browser's width and height. To enable responsive, `isresponsive` property in `e-scrollsettings` should be true. The three modes of responsive layout available in grid based on client width. They are.

* Mobile(<420px)
* Tablet (420px to 617px)
* Desktop(>617px)

N> Default value of `isresponsive` is true.

### Mobile Mode

If client width is less than 420px, the spreadsheet will render in mobile mode. In which, you can see that spreadsheet user interface is customized and redesigned for best view in small screens. The customized feature includes filter dialog, format dialog, chart type dialog and ribbon.

![](Scrolling_images/Scrolling_img2.png)

Ribbon in mobile layout
{:.caption}

![](Scrolling_images/Scrolling_img3.png)

Format cell dialog in mobile layout.
{:.caption}

### Tablet Layout

If the client width is between 420px and 617px, then the spreadsheet will render in tablet mode. Also it has customized the dialogs to match tablet screen size.

![](Scrolling_images/Scrolling_img4.png)

Ribbon in tablet layout.
{:.caption}

## Scroll Mode

Spreadsheet supports two type of modes in scrolling. You can use `scrollmode` property in `e-scrollsettings` to specify the mode of scrolling.

* Normal - This mode doesn't create new row/column when the scrollbar reaches the end.
* Infinite - This mode creates new row/column when the scrollbar reaches the end.

N> Default value of scrollMode property is infinite mode.

## Virtual Scrolling

Spreadsheet has supports for virtual scrolling. This allows you to load data that you require (load data based on viewport size) without buffering the entire huge database. You can set `allowvirtualscrolling` property in `e-scrollsettings` as true to enable virtual scrolling.

N> Default value of `allowvirtualscrolling` property is true.

