---
layout: post
title: Member Editor Paging
description: memebr editor paging
platform: AngularJS
control: pivotclient
documentation: ug
keywords: ejpivotclient, pivotclient, pivotclient widget, js pivotclient 
---

# Member Editor Paging

I> This feature is applicable for OLAP data source only.

Member editor paging helps to improve the rendering performance of the dialog by dividing large amount of data into sections and displaying them.

You can enable member editor paging and set member editor page size in PivotClient control by setting the `e-enableMemberEditorPaging` and `e-memberEditorPageSize` properties.

{% highlight html %}

<div ng-controller="PivotClientCtrl">
    <div id="PivotClient1" ej-pivotclient e-enableMemberEditorPaging="true" e-memberEditorPageSize=100 />
</div>

{% endhighlight %}

Following are the navigation option available in Member Editor Pager.
* Move First - Navigates to the first page.
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Move Last - Navigates to the last page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in numeric value.


![](Member_Editor_images/member_editor.png)