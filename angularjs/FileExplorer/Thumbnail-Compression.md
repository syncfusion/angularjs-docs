---
title: Thumbnail Compression | FileExplorer | JavaScript | Syncfusion
description: Thumbnail image size reduction option in FileExplorer
platform: AngularJS
control: FileExplorer
documentation: UG
keywords: Thumbnail compression, image compression, reduce image size
---

# Thumbnail Compression

The “FileExplorer” allows thumbnail images to be compressed on the server side and loaded into the “FileExplorer” layout to improve performance when working with large size images.

You can enable this option using “**enableThumbnailCompress**” API of FileExplorer. For enabling this API, [showThumbnail](https://help.syncfusion.com/api/js/ejfileexplorer#members:showthumbnail) must be set to true in order to render thumbnail preview of images in Tile and LargeIcons layout.

The [beforeGetImage](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforegetimage) event is triggered before loading a requested image from the server and [getImage](https://help.syncfusion.com/api/js/ejfileexplorer#events:getimage) event is triggered after the requested image is loaded.

Refer following code block that will be helpful to you.

{% highlight html %}

<div id="fileExplorer" ej-fileexplorer e-path="path" e-ajaxaction="ajaxaction" e-layout="tile" e-width="100%" e-enablethumbnailcompress="true" ></div>

{% endhighlight %}

{% highlight javascript %}

    angular.module('FileCtrl', ['ejangular']).controller('FileCtrl', function ($scope) {
        $scope.path = "http://js.syncfusion.com/demos/ejServices/Content/FileBrowser/",
        $scope.ajaxaction = "http://js.syncfusion.com/demos/ejServices/api/FileExplorer/FileOperations"
    });

{% endhighlight %}

N> In server side, don’t forget to add “[GetImage](http://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations~GetImage.html#)” handling operation that helps to reduce the image size before loading.
