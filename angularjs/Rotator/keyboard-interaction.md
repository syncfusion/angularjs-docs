---
layout: post
title: keyboard interaction
description: keyboard interaction
platform: AngularJS
control: rotator
documentation: ug
---

## Keyboard interaction

The Rotator property e-allowkeyboardnavigation turns on keyboard interaction with the Rotator items. You must set this property to ‘true’ to access the keyboard shortcuts. The default value is ‘true’. The value set to this property is Boolean.

The entire Rotator commands are accessed through the keyboard by specifying the Keyboard Shortcut in the following table.

Keyboard shortcuts

<table>
<tr>
<td>
KeyboardShortcut</td><td>
Function</td></tr>
<tr>
<td>
Alt + j</td><td>
Focuses the control</td></tr>
<tr>
<td>
UP</td><td>
Navigates up and left.</td></tr>
<tr>
<td>
Down</td><td>
Navigates down and right.</td></tr>
<tr>
<td>
Left</td><td>
Navigates up and left.</td></tr>
<tr>
<td>
Right</td><td>
Navigates down and right.</td></tr>
<tr>
<td>
Home</td><td>
Navigates to the starting item.</td></tr>
<tr>
<td>
End</td><td>
Navigates to the ending item.</td></tr>
<tr>
<td>
Enter</td><td>
Selects the focused item</td></tr>
</table>
You can refer the following code example for keyboard navigation.

{% highlight html %}



<ul id="sliderContent" ej-rotator e-slideWidth="600px" e-slideHeight="350px" e-showPager="true" e-showCaption="true" e-showThumbnail="thumbnail" e-thumbnailSourceID="thumbnailId" e-showPlayButton="true" e-isResponsive="true">
<li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/green.jpg" title="green" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/snow.jpg" title="snow" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/wheat.jpg" title="wheat" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/tablet.jpg" title="tablet" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/sea.jpg" title="sea" /></li>					</ul>

<ul id="thumbElement" style="display: none">
<li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/green.jpg" title="green" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/snow.jpg" title="snow" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/wheat.jpg" title="wheat" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/tablet.jpg" title="tablet" /></li>
        <li><img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/sea.jpg" title="sea" /></li>					</ul>
</div>



{% endhighlight %}



{% highlight js %}


<script>
angular.module('rotatApp', ['ejangular']).controller('RotatCtrl', function ($scope) {
        });
        $(function () {
            //Control focus key
            $(document).on("keydown", function (e) {
                if (e.altKey && e.keyCode === 74) { // j- key code.
                    $("#slidercontent")[0].focus();
                }
            });
        });

    </script>




{% endhighlight %}



{% highlight css %}


<style type="text/css" class="cssStyles">
       .e-rotator-wrap .e-thumb .e-thumb-items li img {
        width: 130px;
        height: 82px;
    }
</style>



{% endhighlight %}





