---
layout: post
title: Thumb-Scrolling
description: thumb scrolling
platform: AngularJS
control: Scroller
documentation: ug
---

# Thumb Scrolling

Normally the scrollbar position can be changed by dragging the scrollbar handle or clicking the arrows. The **Scroller** control allows you for panning or dragging the scroll content area to drag by dragging inside the scroll content. To achieve this in your **Scroller** control, set **enableTouchScroll** to true. By default the value for **enableTouchScroll** is true. When you want to prevent the panning or dragging the scroll content area, set **enableTouchScroll** as false.

The following steps explains you the configuration of **enableTouchScroll** property in **Scroller**. 

In the HTML page, add a &lt;div&gt; element to configure Scroller widget.

{% highlight html %}

 <div class="control">
        <div id="scrollcontent" ej-scroller e-height="300" e-width="600" e-enabletouchscroll="false">
            <div>
                <div class="sampleContent">
                    <h3 style="font-size: 20px;">MVC</h3>
                    <div>
                        <p>
                            Model–view–controller (MVC) is a software architecture pattern which separates the
                                 representation of information from the user's interaction with it.
                                 The model consists of application data, business rules, logic, and functions. A view can be any
                                 output representation of data, such as a chart or a diagram. Multiple views of the same data 
                                 are possible, such as a bar chart for management and a tabular view for accountants. 
                                 The controller mediates input, converting it to commands for the model or view.The central 
                                 ideas behind MVC are code reusability and n addition to dividing the application into three 
                                 kinds of components, the MVC design defines the interactions between them.
                        </p>
                        <ul>
                            <li>
                                <b>A controller </b>can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document). 
                                    It can also send commands to the model to update the model's state (e.g., editing a document).
                            </li>
                            <li>
                                <b>A model</b> notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands. 
                                    A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.
                            </li>
                            <li>
                                <b>A view</b> requests from the model the information that it needs to generate an output representation to the user.
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>

{% endhighlight %}

{% highlight js %}
    <script>
        angular.module('scrollerrApp', ['ejangular'])
         .controller('ScrollerCtrl', function ($scope) {

         });
    </script>
{% endhighlight %}


The following screenshot displays **Scroller** control with disabled touch support.

![](/js/Scroller/Thumb-Scrolling_images/Thumb-Scrolling_img1.png)

