---
layout: post
title: Multiple Selection
description: FileExplorer allows the user to select multiple files
platform: AngularJS
control: File Explorer
documentation: ug
---


# Multiple Selection

The FileExplorer allows the user to select multiple files by enabling the [allowMultiSelection](https://help.syncfusion.com/api/js/ejfileexplorer#members:allowmultiselection) property. The multiple selection can be done by pressing the **Ctrl** key or **Shift** key. You can select all the files in the directory by pressing “**Ctrl + A**”. The multiple selection is useful on copy pasting multiple files, deleting multiple files and downloading multiple files. In another way, multiple files can be selected by mouse down and drag over the desired files. In addition to that, additional files can be selected with the preselected file by holding the ctrl/shift key and drag the mouse over the files. Also, holding the ctrl/shift key and dragging over selected files will unselect the selected files.

The [select](https://help.syncfusion.com/api/js/ejfileexplorer#events:select) event will be triggered when the items of FileExplorer control is selected.
Also [unselect](https://help.syncfusion.com/api/js/ejfileexplorer#events:unselect) event will be triggered when the items of FileExplorer control is unselected.

N>  For selecting files by mouse down and drag set `allowMultiSelection` property as true.


{% highlight html %}

<div id="fileExplorer" ej-fileexplorer e-path="path" e-ajaxaction="ajaxaction" e-isresponsive="true" e-allowmultiselection="true" ></div>
<!--allowMultiSelection property is true by default-->

{% endhighlight %}

{% highlight javascript %}

    angular.module('FileCtrl', ['ejangular']).controller('FileCtrl', function ($scope) {
        $scope.path = "http://js.syncfusion.com/demos/ejServices/Content/FileBrowser/",
        $scope.ajaxaction = ""http://js.syncfusion.com/demos/ejServices/api/FileExplorer/FileOperations"
    });

{% endhighlight %}
