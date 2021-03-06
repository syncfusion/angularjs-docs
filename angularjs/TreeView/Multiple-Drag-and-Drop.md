---
layout: post
title: Multiple-Drag-and-Drop
description: multiple drag and drop
platform: AngularJS
control: TreeView
documentation: ug
---


# Drag and Drop Multiple Nodes

TreeView supports to drag and drop multiple nodes by specifying [allowMultiSelection](http://help.syncfusion.com/api/js/ejtreeview#members:allowmultiselection) as true along with [allowDragAndDrop](https://help.syncfusion.com/api/js/ejtreeview#members:allowdraganddrop) as true. It allows you to drag and drop multiple nodes in TreeView.

{% highlight html %}

	<!--create the TreeView wrapper-->
	<table>
		<tr>
			<td>
				<div id="treeViewdrag" e-treeview e-fields-datasource="tree1" e-fields-id="id" e-fields-parentid="parent" e-fields-text="text" e-allowmultiselection="true" e-allowdraganddrop="true" /> 
			</td>
			<td>
			    <div id="treeViewdrop" e-treeview e-fields-datasource="tree2" e-fields-id="id" e-fields-parentid="parent" e-fields-text="text" e-allowmultiselection="true" e-allowdraganddrop="true" />
			</td>
		</tr>
	</table>

{% endhighlight %}

{% highlight js %}

	var tree1 = [

		{ id: 1, text: "Item 1" },
	
		{ id: 2, text: "Item 2" },
	
		{ id: 3, text: "Item 3" },
	
		{ id: 4, text: "Item 4" },
	
		{ id: 5, parent: 1, text: "Item 1.1" },
	
		{ id: 6, parent: 1, text: "Item 1.2" },
	
		{ id: 7, parent: 1, text: "Item 1.3" },
	
		{ id: 8, parent: 3, text: "Item 3.1" },
	
		{ id: 9, parent: 3, text: "Item 3.2" },
	
		{ id: 10, parent: 5, text: "Item 1.1.1" }
	
	];
	
	var tree2 = [
	
		{ id: 11, text: "Item 5" },
	
		{ id: 12, text: "Item 6" },
	
		{ id: 13, text: "Item 7" },
	
		{ id: 14, text: "Item 4" },
	
		{ id: 15, parent: 11, text: "Item 5.1" },
	
		{ id: 16, parent: 11, text: "Item 5.2" },
	
		{ id: 17, parent: 11, text: "Item 5.3" },
	
		{ id: 18, parent: 13, text: "Item 7.1" },
	
		{ id: 19, parent: 13, text: "Item 7.2" },
	
		{ id: 10, parent: 15, text: "Item 5.1.1" }
	
	];
	
{% endhighlight %}

For more details about multiple drag and drop in TreeView, refer the sample [here](http://jsplayground.syncfusion.com/Sync_1mo2awgk).

