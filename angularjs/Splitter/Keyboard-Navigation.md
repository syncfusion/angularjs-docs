---
layout: post
title: Syncfusion Splitter Keyboard-Navigation
description: keyboard navigation
platform: AngularJS
control: Splitter
documentation: ug
---

# Keyboard Navigation

With the keyboard navigation enabled in the Splitter component, it is possible to control the actions of the Splitter with the provided shortcut keys. Almost all the Splitter actions that are done by mouse can be controlled with shortcut keys.

The various keyboard shortcuts available within the Splitter component are discussed in the following table.

Keyboard Shortcuts:


<table>
<tr>
<th>
Shortcut Key</th><th>
Description</th></tr>
<tr>
<td>
Left</td><td>
Moves the Split bar left. </td></tr>
<tr>
<td>
Right</td><td>
Moves the Split bar right. </td></tr>
<tr>
<td>
Ctrl + Left</td><td>
Collapses the left pane.</td></tr>
<tr>
<td>
Ctrl + Right</td><td>
Collapses the right pane.</td></tr>
<tr>
<td>
Up</td><td>
Moves the Split bar up.</td></tr>
<tr>
<td>
Down</td><td>
Moves the Split bar down.</td></tr>
<tr>
<td>
Ctrl + Up</td><td>
Collapses the top pane.</td></tr>
<tr>
<td>
Ctrl + Down</td><td>
Collapses the bottom pane.</td></tr>
<tr>
<td>
Enter</td><td>
Resize the pane to the current Split bar position.</td></tr>
<tr>
<td>
Esc</td><td>
Focuses out from the Split bar.</td></tr>
</table>

## Configuring Keyboard Navigation

The following steps explain to enable keyboard interaction for **Splitter** component.

In the **HTML** page set the corresponding **&lt;div&gt;** element for rendering **Splitter** component. 

{% highlight html %}

    <div id="splitter" ej-splitter e-width="600" e-height="280">
        <div>
            <div style="padding: 0px 15px;">
                <h3 class="h3">Tools </h3>
                Essential Tools is an collection of user interface components used to create interactive
                ASP.NET MVC applications.
            </div>
        </div>
        <div>
            <div style="padding: 0px 15px;">
                <h3 class="h3">Grid </h3>
                Essential MVC Grid offers full featured a Grid control with extensive support for
                Grouping and the display of hierarchical data.
            </div>
        </div>
    </div>

{% endhighlight %}


To control the focus key by using keyCode of “altKey” and “j” key in document key down function. Declare the keydown function in script section.


{% highlight javascript %}


    angular.module('syncApp', ['ejangular'])
            .controller('SplitterCtrl', function ($scope) {

            })
    $(document).on("keydown", function (e) {
        if (e.altKey && e.keyCode === 74) { // j- key code.
            $("#splitter .e-splitbar")[0].focus();
        }
    });

{% endhighlight %}

Run the sample and press **Alt + J** to focus the Splitter component. Perform provided functionality by using keyboard shortcuts.

![Keyboard Navigation](Keyboard-Navigation_images\Keyboard-Navigation_img1.png) 

