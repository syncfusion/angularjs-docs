---
Layout: Post
Title: Editing with Grid widget for the Syncfusion Essential AngularJS
Description: How to perform editing and configure edit time functionalities like edit type, edit time controls, etc
Platform: AngularJS
Control: Grid
Documentation: UG
--- 
# Editing

The grid control supports dynamic insertion, updation, and deletion of records. You can start the edit action either by double clicking the particular row or by selecting the required row and clicking the edit icon in toolbar. Similarly, you can add new record to grid either by clicking the insert icon in toolbar or external button which is bound to call method [`addRecord`](http://help.syncfusion.com/api/js/ejgrid#methods:addrecord "addRecord") of grid.  `Save` and `Cancel` on edit mode can be possible using respective toolbar icon in grid.

You can delete the record by selecting a required row and clicking delete icon in the toolbar. 

The primary key for the data source should be defined in [`e-columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns") for proper editing. In [`e-columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns") definition, particular primary column's [`e-isprimarykey`](http://help.syncfusion.com/api/js/ejgrid#members:columns-isprimarykey "isPrimaryKey") property should be set to `true`. Refer to the Knowledge base [link](http://www.syncfusion.com/kb/2675/cant-edit-any-row-except-the-first-row-in-grid# "link") for more information.

N> 1. In grid, the primary key column will be automatically set to read-only while editing the row, but you can specify primary key column value while adding a new record.
N> 2. The column which is specified as [`e-isidentity`](http://help.syncfusion.com/api/js/ejgrid#members:columns-isidentity "isIdentity") will be in read-only mode both while editing and adding a record. Also, auto incremented value is assigned to that [`e-isidentity`](http://help.syncfusion.com/api/js/ejgrid#members:columns-isidentity "isIdentity") column.

## Toolbar with edit option

Using toolbar that is rendered at the top of the grid header, you can show all the CRUD related action. To enable toolbar and toolbar items, set the [`showToolbar`](http://help.syncfusion.com/api/js/ejgrid#members:toolbarsettings-showtoolbar "showToolbar") property to true and [`toolbarItems`](http://help.syncfusion.com/api/js/ejgrid#members:toolbarsettings-toolbaritems "toolbarItems"). The default toolbar items are `add`, `edit`, `delete`, `update` and `cancel`.

N> For the [`toolbarItems`](http://help.syncfusion.com/api/js/ejgrid#members:toolbarsettings-toolbaritems "toolbarItems") property you can assign either `string` value ("add") or `enum` value (`ej.Grid.ToolBarItems.Add`).

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="ToolbarCtrl">
     <div id="Grid" ej-grid e-datasource="data"  e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
             <div e-column e-field="OrderID" e-isprimarykey="true"></div>
             <div e-column e-field="CustomerID" ></div>
             <div e-column e-field="EmployeeID" ></div>
             <div e-column e-field="ShipCity" ></div>
             <div e-column e-field="ShipCountry"></div>
          </div>
      </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
        syncApp.controller('ToolbarCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img1.png)


## Cell edit type and its params

The edit type of bound column can be customized using the [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType") property of [`e-columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns"). The following Essential JavaScript controls are supported built-in by [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType"). You can set the [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType") based on specific data type of the column. 

* [`CheckBox`](http://help.syncfusion.com/api/js/ejcheckbox# "CheckBox") control for boolean data type.
* [`NumericTextBox`](http://help.syncfusion.com/api/js/ejtextboxes# "NumericTextBox") control for integers, double, and decimal data types.
* [`InputTextBox`] control for string data type.
* [`DatePicker`](http://help.syncfusion.com/api/js/ejdatepicker# "DatePicker") control for date data type.
* [`DateTimePicker`](http://help.syncfusion.com/api/js/ejdatetimepicker# "DateTimePicker") control for date-time data type.
* [`DropDownList`](http://help.syncfusion.com/api/js/ejdropdownlist# "DropDownList") control for list of data type.



You can define the model for all the editTypes controls while editing through the [`e-editparams`](http://help.syncfusion.com/api/js/ejgrid#members:columns-editparams "editParams") property of [`columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns").

The following table describes [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType") and their corresponding [`e-editparams`](http://help.syncfusion.com/api/js/ejgrid#members:columns-editparams "editParams") of the specific data type of the column.

<table>
<tr>
<th>
EditType</th><th>
EditParams</th><th>
Example</th></tr>
<tr>
<td>
CheckBox</td><td>
{{ '[ejCheckBox](http://help.syncfusion.com/api/js/ejcheckbox)' | markdownify }} </td><td>
editParams: { checked: true }</td></tr>
<tr>
<td>
NumericTextBox </td><td>
{{ '[ejTextBoxes](http://help.syncfusion.com/api/js/ejtextboxes)' | markdownify }} </td><td>
editParams: { decimalPlaces: 2, value:5  }</td></tr>
<tr>
<td>
InputTextBox </td><td>
-</td><td>
-</td></tr>
<tr>
<td>
DatePicker </td><td>
{{ '[ejDatePicker](http://help.syncfusion.com/api/js/ejdatepicker)' | markdownify }} </td><td>
editParams: {  buttonText : "Now" }</td></tr>
<tr>
<td>
DateTimePicker</td><td>
{{ '[ejDateTimePicker](http://help.syncfusion.com/api/js/ejdatetimepicker)' | markdownify }} </td><td>
editParams: {  enabled: true }</td></tr>
<tr>
<td>
DropDownList</td><td>
{{ '[ejDropDownList](http://help.syncfusion.com/api/js/ejdropdownlist)' | markdownify }} </td><td>
editParams: {  allowGrouping: true }</td></tr>

</table>

N> 1. If [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType") is not set, then by default it will display the input element ("stringedit") while editing a column.
N> 2. For [`e-edittype`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittype "editType") property you can assign either `string` value ("numericedit") or `enum` value (`ej.Grid.EditingType.Numeric`).

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="EditTypeCtrl">
     <div id="Grid" ej-grid e-datasource="data"  e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" e-edittype="stringedit" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-editparams-decimalplaces="2" ></div>
              <div e-column e-field="ShipCity" e-edittype="dropdownedit" e-editparams-enableAnimation="true" ></div>
              <div e-column e-field="ShipCountry"></div>
			  <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}"></div>
			  <div e-column e-field="Verified" e-edittype="booleanedit" e-editparams-showroundedcorner="true" ></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
       syncApp.controller('EditTypeCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });      
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img2.png)


## Cell Edit Template

When you edit the column values, custom editor can be created by using the [`e-edittemplate`](http://help.syncfusion.com/api/js/ejgrid#members:columns-edittemplate "editTemplate") property of [`e-columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns"). It has three functions, they are

1. `create`: Used to create the control at time of initialize.
2. `read`: Used to read the input value at time of save.
3. `write`: Used to assign the value to control at time of editing.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="EditTemplateCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
			  <div e-column e-field="Freight"></div>
              <div e-column e-field="ShipCountry"></div>
			  <div e-column e-field="ShipPostalCode" e-edittemplate="editTemp"></div>
		  </div>
      </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
       syncApp.controller('EditTemplateCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] };
          $scope.editTemp = {
                create: function () {
                    return "<input>";
                },
                write: function (args) {
                    args.element.ejMaskEdit({
                        maskFormat: "99-99-9999",
                        value: args.rowdata["ShipPostalCode"]
                    });
                },
                read: function (args) {
                    return args.ejMaskEdit("get_UnstrippedValue");
                },

            };
      });      
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img3.png)


## Edit Modes

### Inline 

Set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") as `normal`, then the row itself is changed as edited row.

N> For [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") property you can assign either `string` value ("normal") or `enum` value (`ej.Grid.EditMode.Normal`).

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="InlineCtrl">
     <div id="Grid" ej-grid e-datasource="data"  e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
              <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}"></div>
		  </div>
       </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
      syncApp.controller('InlineCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"normal"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img4.png)


### Inline Form

Set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") as `inlineform`, then edit form will be inserted next to the row which is to be edited.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="InlineFormCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
              <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}"></div>
		  </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('InlineFormCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"inlineform"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img5.png)


### Inline Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using Inline template form, set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") to `inlineformtemplate` and specify the template ID to [`inlineFormTemplateID`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-inlineformtemplateid "editSettings.inlineFormTemplateID") of [`e-editsettings`] prop

While using template form, you can change the HTML elements to appropriate JS controls based on the column type. This can be achieved by using [`actionComplete`](http://help.syncfusion.com/api/js/ejgrid#events:actioncomplete "actionComplete") event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while saving the edited record.
N> 3.  It's a standard way to enclose the `template` within the `script` tag with `type` as "text/ng-template".
N> 4.  For [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") property you can assign either `string` value ("inlineformtemplate") or `enum` value (`ej.Grid.EditMode.InlineTemplateForm`) 

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="InlineTemplateCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" e-actioncomplete="actionComplete">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="ShipCity"></div>
          </div>
     </div>
 </div>
 
   <script id="template" type="text/ng-template">
        <table cellspacing="10">
            <tr>
                <td>Order ID</td>
                <td>
                    <input id="OrderID" name="OrderID" disabled="disabled" ngModel="{{"{{"}}:OrderID{{}}}}" value="{{"{{"}}:OrderID{{}}}}"/>
                </td>
                <td>Customer ID</td>
                <td>
                    <input id="CustomerID" name="CustomerID" ngModel="{{"{{"}}:CustomerID{{}}}}" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
                </td>
            </tr>
            <tr>
                <td>Employee ID</td>
                <td>
                    <input type="text" id="EmployeeID" name="EmployeeID" ngModel="{{"{{"}}:EmployeeID{{}}}}" value="{{"{{"}}:EmployeeID{{}}}}"/>
                </td>
                <td>Ship City</td>
                <td>
                    <select id="ShipCity" name="ShipCity">
                        <option value="Argentina">Argentina</option>
                        <option value="Austria">Austria</option>
                        <option value="Belgium">Belgium</option>
                        <option value="Brazil">Brazil</option>
                        <option value="Canada">Canada</option>
                        <option value="Denmark">Denmark</option>
                    </select>
                </td>
            </tr>
        </table>
    </script>
{% endhighlight %}

{% highlight javascript %}
       syncApp.controller('InlineTemplateCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true,editMode: "inlineformtemplate", inlineFormTemplateID: "#template" };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] };
		  $scope.actionComplete = function (args) {
                $("#EmployeeID").ejNumericTextbox();
                $("#Freight").ejNumericTextbox();
                $("#ShipCity").ejDropDownList();
            }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img6.png)

{:caption}
Before the template elements are converted to JS controls


![](Editing_images/Editing_img7.png)
{:caption}
After the template elements are converted to JS controls using actionComplete event 


### Dialog

Set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") as `dialog` to edit data using a dialog box, which displays the fields associated with the data record being edited.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="DialogCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" >
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
              <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}"></div>
		  </div>
       </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('DialogCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"dialog"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img8.png)


### Dialog Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using Inline template form, set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") to dialogtemplate and specify the template id to the [`dialogEditorTemplateID`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-dialogeditortemplateid "dialogEditorTemplateID") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings").

While using template, you can change the elements that are defined in the `template`, to appropriate JS controls based on the column type. This can be achieved by using [`actionComplete`](http://help.syncfusion.com/api/js/ejgrid#events:actioncomplete "actionComplete") event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") property you can assign either `string` value ("dialogtemplate") or `enum` value (`ej.Grid.EditMode.DialogTemplate`).

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="DialogTemplateCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" e-actioncomplete="actionComplete">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="ShipCity"></div>
          </div>
     </div>
 </div>
 <script id="template" type="text/ng-template">
        <table cellspacing="10">
            <tr>
                <td>Order ID</td>
                <td>
                    <input id="OrderID" name="OrderID" disabled="disabled" ngModel="{{"{{"}}:OrderID{{}}}}" value="{{"{{"}}:OrderID{{}}}}"/>
                </td>
                <td>Customer ID</td>
                <td>
                    <input id="CustomerID" name="CustomerID" ngModel="{{"{{"}}:CustomerID{{}}}}" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
                </td>
            </tr>
            <tr>
                <td>Employee ID</td>
                <td>
                    <input type="text" id="EmployeeID" name="EmployeeID" ngModel="{{"{{"}}:EmployeeID{{}}}}" value="{{"{{"}}:EmployeeID{{}}}}"/>
                </td>
                <td>Ship City</td>
                <td>
                    <select id="ShipCity" name="ShipCity">
                        <option value="Argentina">Argentina</option>
                        <option value="Austria">Austria</option>
                        <option value="Belgium">Belgium</option>
                        <option value="Brazil">Brazil</option>
                        <option value="Canada">Canada</option>
                        <option value="Denmark">Denmark</option>
                    </select>
                </td>
            </tr>
        </table>
    </script>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('DialogTemplateCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true,editMode: "dialogtemplate",  dialogEditorTemplateID: "#template" };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] };
		  $scope.actionComplete = function (args) {
                $("#EmployeeID").ejNumericTextbox();
                $("#Freight").ejNumericTextbox();
                $("#ShipCity").ejDropDownList();
            }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img9.png)
{:caption}
Before the template elements are converted to JS controls

![](Editing_images/Editing_img10.png)
{:caption}
After the template elements are converted to JS controls using actionComplete event 

### External Form

By setting the [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") as externalform, the edit form is opened outside the grid content.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="ExternalFormCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" e-pagesettings-pagesize="7">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true" ></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
              <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}"></div>
		   </div>
       </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
       syncApp.controller('ExternalFormCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"externalform"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example.

![](Editing_images/Editing_img11.png)


Form Position:

You can position an external edit form at the following two positions:

1. Top right
2. Bottom left

This can be achieved by setting the [`formPosition`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-formposition "formPosition") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings") to "topright" or "bottomleft".

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="FormCtrl">
     <div id="Grid" ej-grid e-datasource="data"  e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" e-pagesettings-pagesize="7">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
      syncApp.controller('PhoneListCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"externalform", formPosition:"topRight"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img12.png)


### External Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using External template form, set [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") to externalformtemplate and specify the template id to [`externalFormTemplateID`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-externalformtemplateid "externalFormTemplateID") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings").

While using template, you can change the elements that are defined in the template, to appropriate JS controls based on the column type. This can be achieved by using [`actionComplete`](http://help.syncfusion.com/api/js/ejgrid#events:actioncomplete "actionComplete") event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For the [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") property you can assign either `string` value ("externalformtemplate") or `enum` value (`ej.Grid.EditMode.ExternalFormTemplate`).

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="ExternalTemplateCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems" e-pagesettings-pagesize="5" e-actioncomplete="actionComplete">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="ShipCity"></div>
          </div>
     </div>
 </div>
 <script id="template" type="text/ng-template">
        <table cellspacing="10">
            <tr>
                <td>Order ID</td>
                <td>
                    <input id="OrderID" name="OrderID" disabled="disabled" ngModel="{{"{{"}}:OrderID{{}}}}" value="{{"{{"}}:OrderID{{}}}}"/>
                </td>
                <td>Customer ID</td>
                <td>
                    <input id="CustomerID" name="CustomerID" ngModel="{{"{{"}}:CustomerID{{}}}}" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
                </td>
            </tr>
            <tr>
                <td>Employee ID</td>
                <td>
                    <input type="text" id="EmployeeID" name="EmployeeID" ngModel="{{"{{"}}:EmployeeID{{}}}}" value="{{"{{"}}:EmployeeID{{}}}}"/>
                </td>
                <td>Ship City</td>
                <td>
                    <select id="ShipCity" name="ShipCity">
                        <option value="Argentina">Argentina</option>
                        <option value="Austria">Austria</option>
                        <option value="Belgium">Belgium</option>
                        <option value="Brazil">Brazil</option>
                        <option value="Canada">Canada</option>
                        <option value="Denmark">Denmark</option>
                    </select>
                </td>
            </tr>
        </table>
    </script>
{% endhighlight %}

{% highlight javascript %}
        syncApp.controller('ExternalTemplateCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true,editMode: "externalformtemplate",  externalFormTemplateID: "#template" };
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] };
		  $scope.actionComplete = function (args) {
                $("#EmployeeID").ejNumericTextbox();
                $("#Freight").ejNumericTextbox();
                $("#ShipCity").ejDropDownList();
            }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img13.png)
{:caption}
Before the template elements are converted to JS controls

![](Editing_images/Editing_img14.png)
{:caption}
After the template elements are converted to JS controls using actionComplete event

### Batch / Excel-like

You can start to edit by clicking a cell and typing data into it. Edited cell will be marked while navigating to next cell or any other row, so that you know which fields or cells has been edited. Set the [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode") to `batch` to enable batch editing.

N> `getBatchChanges` method of grid holds the unsaved record changes.
N> Refer to the KB [link](http://www.syncfusion.com/kb/3016/how-to-suppress-grid-confirmation-messages# "link") for "How to suppress grid confirmation messages" in batch mode.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="BatchCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
             <div e-column e-field="OrderID" e-isprimarykey="true"></div>
             <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
			  <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}" ></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('BatchCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"batch"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img15.png)


## Confirmation messages

To show the confirm dialog while saving or discarding the batch changes (discarding during the grid action like filtering, sorting and paging), set [`showConfirmDialog`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-showconfirmdialog "showConfirmDialog") to `true`.

N> [`showConfirmDialog`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-showconfirmdialog "showConfirmDialog") property is only for batch editing mode.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="BatchCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true" ></div>
              <div e-column e-field="CustomerID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
			  <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}" ></div>
           </div>
      </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
        syncApp.controller('BatchCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true , editMode:"batch",showConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      });  
{% endhighlight %}

The following output is displayed as a result of the previous code example:

![](Editing_images/Editing_img16.png)


To show delete confirm dialog while deleting a record, set the [`showDeleteConfirmDialog`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-showdeleteconfirmdialog "showDeleteConfirmDialog") to true.

N> [`showDeleteConfirmDialog`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-showdeleteconfirmdialog "showDeleteConfirmDialog") property is for all type of [`editMode`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-editmode "editMode").

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="EditingCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry" e-edittype="dropdownedit" ></div>
			  <div e-column e-field="OrderDate" e-edittype="datepicker" e-format="{0:MM/dd/yyyy}" ></div>
           </div>
      </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('EditingCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showDeleteConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      }); 
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img17.png)


## Column Validation

You can validate the value of the added or edited record cell before saving.

The below validation script files are needed when editing is enabled with validation:

1. jquery.validate.min.js
2. jquery.validate.unobtrusive.min.js
 
 
### jQuery Validation


You can set the validation rules using the [`validationRules`](http://help.syncfusion.com/api/js/ejgrid#members:columns-validationrules "validationRules") property of [`columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns"). The following are jQuery validation methods:

__List__ __of__ __Jquery__ __validation__ __methods__

<table>
<tr>
<th>
Rules</th><th>
Description</th></tr>
<tr>
<td>
required</td><td>
Requires an element.</td></tr>
<tr>
<td>
remote</td><td>
Requests a resource to check the element for validity.</td></tr>
<tr>
<td>
minlength</td><td>
Requires the element to be of given minimum length.</td></tr>
<tr>
<td>
maxlength</td><td>
Requires the element to be of given maximum length.</td></tr>
<tr>
<td>
range</td><td>
Requires the element to be in given value range.</td></tr>
<tr>
<td>
min</td><td>
The element requires a given minimum.</td></tr>
<tr>
<td>
max</td><td>
The element requires a given maximum.</td></tr>
<tr>
<td>
range</td><td>
Requires the element to be in a given value range.</td></tr>
<tr>
<td>
email</td><td>
The element requires a valid email.</td></tr>
<tr>
<td>
url</td><td>
The element requires a valid URL</td></tr>
<tr>
<td>
date</td><td>
Requires the element to be a date.</td></tr>
<tr>
<td>
dateISO</td><td>
The element requires an ISO date.</td></tr>
<tr>
<td>
number</td><td>
The element requires a decimal number.</td></tr>
<tr>
<td>
digits</td><td>
The element requires digits only.</td></tr>
<tr>
<td>
creditcard</td><td>
Requires the element to be a credit card number.</td></tr>
<tr>
<td>
equalTo</td><td>
Requires the element to be the same as another.</td></tr>
</table>

Grid supports all the standard validation methods of jQuery, please refer the jQuery validation documentation [link](http://jqueryvalidation.org/documentation/# "link") for more information.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="ValidationCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true" e-validationrules-required="true"></div>
              <div e-column e-field="CustomerID" e-validationrules-minlength="3"></div>
              <div e-column e-field="ShipCity"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-validationrules-range="0, 1000"></div>
              <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     syncApp.controller('ValidationCtrl', function ($scope,$rootScope) {
        //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showDeleteConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
      }); 
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img18.png)


## Persisting data in Server

Edited data can be persisted in database using RESTful web services. 

All the CRUD operations in grid are done through DataManager. DataManager have an option to bind all the CRUD related data in server side. Please refer the ['link'](http://help.syncfusion.com/js/datamanager/overview# "link") to know about the DataManager.

For your information, ODataAdaptor persist data in server as per OData protocol.

The following section explains how to get the edited data details at the server side using the URLAdaptor:

### URL Adaptor

You can use the `UrlAdaptor` of [`ejDataManger`](http://help.syncfusion.com/api/js/ejdatamanager# "ejDataManger") when binding datasource from remote data. At initial load of Grid, using the URL property of DataManager, data are fetched from remote data and bound to Grid. You can map CRUD operation in Grid to Server-Side Controller action using the properties `insertUrl`, `removeUrl`, `updateUrl`, `crudUrl`, and `batchUrl`.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="AdaptorCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
              <div e-column e-field="EmployeeID"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-format="{0:C}"></div>
              <div e-column e-field="ShipName"></div>
			  <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
 
{% endhighlight %}

{% highlight javascript %}
 
    var dataManger = ej.DataManager({
          url: "/Home/DataSource",
          adaptor: "UrlAdaptor",
          updateUrl : "/Home/Update",
	      insertUrl : "/Home/Insert",
		  removeUrl : "/Home/Delete",
    });

     syncApp.controller('AdaptorCtrl', function ($scope,$rootScope) {
          $scope.data = dataManger;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showDeleteConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 

{% endhighlight %}

When you use `UrlAdaptor`, you need to return the data as `JSON` and the JSON object must contain a property as `result` with dataSource as its value and one more property `count` with the dataSource total records count as its value.

The following code example describes the previous behavior.

{% highlight cs %}
public ActionResult DataSource(DataManager dm)
{
	IEnumerable DataSource = OrderRepository.GetAllRecords();
	DataResult result = new DataResult();
	DataOperations operation = new DataOperations();
	result.result = DataSource;
	result.count = result.result.AsQueryable().Count();
	if (dm.Skip > 0)
		result.result = operation.PerformSkip(result.result, dm.Skip);
	if (dm.Take > 0)
		result.result = operation.PerformTake(result.result, dm.Take);
	return Json(result, JsonRequestBehavior.AllowGet);
}
public class DataResult
{
	public IEnumerable result { get; set; }
	public int count { get; set; }
}
{% endhighlight %}

The grid actions (sorting, filtering, paging, searching, and aggregates) details are obtained in the 'DataManager' class. While initializing the grid, paging only enabled. The following screenshot shows paging details that are bound to the DataManager class.


![](Editing_images/Editing_img20.png)


Using the 'DataOperations' helper class, you can perform grid action at server side. The in-built methods that we have provided in the DataOperations class are listed as follows:

1. PerformSorting
2. PerformFiltering
3. PerformSearching
4. PerformSkip
5. PerformTake
6. PerformWhereFilter
7. PerformSelect
8. Execute

### Accessing CRUD action request details in server side:

The 'Server-Side' function must be declared with the following parameter name for each editing functionality.

Parameters Table

<table>
        <tr>
            <th>
                Action
            </th>
            <th>
                Parameter Name</th>
            <th>
                Example
            </th>
        </tr>
        <tr>
            <td rowspan="2">
                Update,Insert
            </td>
            <td>
                value
            </td>
            <td rowspan="2">
                public ActionResult Update(EditableOrder value){ }
            </td>
        </tr>
        <tr>
           
            <td>
                public ActionResult Insert(EditableOrder value){ }
            </td>
        </tr>
        <tr>
            <td>
                Remove
            </td>
            <td>
                key
            </td>
            <td>
                public ActionResult Remove(int key){ }
            </td>
        </tr>
        <tr>
            <td>
                Batch Add
            </td>
            <td>
                added
            </td>
            <td rowspan="3">
                public ActionResult BatchUpdate(string action, List &lt;editableorder&gt; added, List &lt;editableorder&gt; changed, List &lt;editableorder&gt; deleted, int? key){ }
            </td>
        </tr>
        <tr>
            <td>
                Batch Update
            </td>
            <td>
                changed
            </td>
            
        </tr>
        <tr>
            <td>
                Batch Delete
            </td>
            <td>
                deleted
            </td>
           
        </tr>
        <tr>
            <td>
                Crud Update,Crud Insert
            </td>
            <td>
                value, action
            </td>
            <td>
                public ActionResult CrudUrl(EditableOrder value, string action){ }
            </td>
        </tr>
        <tr>
            <td>
                Crud Remove
            </td>
            <td>
                action, key, keyColumn
            </td>
            <td>
               public ActionResult CrudUrl(string action, int? key, string keyColumn){ }
            </td>
        </tr>
		<tr>
            <td>
               Crud Remove - Multi Delete
            </td>
            <td>
                action, key, deleted
            </td>
            <td>
               public ActionResult CrudUrl(string action, string key, List <EditableOrder> deleted){ }
            </td>
        </tr>
    </table>

	
### Insert Record:

Using the `insertUrl` property, you can specify the controller action mapping URL to perform insert operation at server side.

The following code example describes the previous behavior.

{% highlight cs %}
public ActionResult Insert(EditableOrder value)
{
    OrderRepository.Add(value);
    var data = OrderRepository.GetAllRecords();
    return Json(value, JsonRequestBehavior.AllowGet);
}
{% endhighlight %}

The newly added record details are bound to the 'value' parameter. Please refer to the following image:


![](Editing_images/Editing_img21.png)


### Update Record:

Using the `updateUrl` property, you can specify the controller action mapping URL to perform save/update operation at server side.

The following code example describes the previous behavior.

{% highlight cs %}
public ActionResult Update(EditableOrder value)
{
    OrderRepository.Update(value);
    var data = OrderRepository.GetAllRecords();
    return Json(value, JsonRequestBehavior.AllowGet);
}
{% endhighlight %}

The updated record details are bound to the 'value' parameter. Please refer to the following image:

![](Editing_images/Editing_img22.png)


### Delete Record:

Using the `removeUrl` property, you can specify the controller action mapping URL to perform delete operation at server side.

The following code example describes the previous behavior.

{% highlight cs %}
public ActionResult Remove(int key)
{
  OrderRepository.Delete(key);
  var data = OrderRepository.GetAllRecords();
  return Json(key, JsonRequestBehavior.AllowGet);
}
{% endhighlight %}

The deleted record primary key value is bound to the 'key' parameter. Please refer to the following image:

![](Editing_images/Editing_img23.png)


### CRUD URL:

Instead of specifying separate controller action method for CRUD (insert, update and delete)operation, using the `crudUrl` property, you can specify the controller action mapping URL to perform all the CRUD operation at server side using single method.

The action parameter of `crudUrl` is used to get the corresponding CRUD action.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="AdaptorCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID" ></div>
              <div e-column e-field="EmployeeID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-format="{0:C}" ></div>
              <div e-column e-field="ShipName" ></div>
			  <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
 
 {% endhighlight %}

{% highlight javascript %}
    
    var dataManger = ej.DataManager({
          url: "/Home/DataSource",
          adaptor: "UrlAdaptor",
          crudUrl : "Home/CrudUpdate",
	  });

     syncApp.controller('AdaptorCtrl', function ($scope,$rootScope) {
          $scope.data = dataManger;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showDeleteConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 

{% endhighlight %}

{% highlight cs %}
public ActionResult CrudUpdate(EditableOrder value, string action, int key)
{
    if (action == "update")
        OrderRepository.Update(value);
    else if (action == "insert")
        OrderRepository.Add(value);
    else if (action == "remove")
        OrderRepository.Delete(key);
    return Json(value, JsonRequestBehavior.AllowGet);
}
{% endhighlight %}

Please refer to the following image to know about the action parameter:

![](Editing_images/Editing_img24.png)


N>  If you specify `insertUrl` along with `CrudUrl`, the `insertUrl` will alone be called when record add action is performed in the grid.

### Batch URL:

The `batchUrl` property supports only for batch editing mode. You can specify the controller action mapping URL to perform Batch operation at server side.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="AdaptorCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true" ></div>
              <div e-column e-field="CustomerID" ></div>
              <div e-column e-field="EmployeeID" ></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-format="{0:C}" ></div>
              <div e-column e-field="ShipName" ></div>
			  <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
 {% endhighlight %}


 {% highlight javascript %}

     var dataManger = ej.DataManager({
          url: "/Home/DataSource",
          adaptor: "UrlAdaptor",
          batchUrl : "Home/BatchUpdate"
	  });

     syncApp.controller('AdaptorCtrl', function ($scope,$rootScope) {
          $scope.data = dataManger;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showDeleteConfirmDialog:true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 

{% endhighlight %}


{% highlight cs %}

public ActionResult BatchUpdate(string action, List<EditableOrder> added, List<EditableOrder> changed, List<EditableOrder> deleted, int? key)
{
    if (changed != null)
        OrderRepository.Update(changed);
    if (deleted != null)
        OrderRepository.Delete(deleted);
    if (added != null)
        OrderRepository.Add(added);
    var data = OrderRepository.GetComplexRecords();
    return Json(new { changed = changed, added = added, deleted = deleted }, JsonRequestBehavior.AllowGet);
}

{% endhighlight %}


Please refer to the following image for more information about batch parameters:

![](Editing_images/Editing_img25.png)


## Adding New Row Position

To add new row in the top or bottom position of grid content, set [`rowPosition`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-rowposition "rowPosition") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings") depending on the requirement.

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="EditingCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
              <div e-column e-field="ShipCity"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     
      syncApp.controller('EditingCtrl', function ($scope,$rootScope) {
         //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,rowPosition:"bottom"};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 
{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img26.png)


## Render with blank row for easy add new

The blank add new row is displayed in the grid content during grid initialization itself to add a new record easily. To enable show add new row by default, set [`showAddNewRow`](http://help.syncfusion.com/api/js/ejgrid#members:showaddnewrow "showAddNewRow") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings") to `true`.

The blank add new row is displayed either in the top or bottom of the corresponding page, its position is based on the [`rowPosition`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-rowposition "rowPosition") property of [`editSettings`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings "editSettings").

The following code example describes the previous behavior.

{% highlight html %}
<div ng-controller="EditingCtrl">
     <div id="Grid" ej-grid e-datasource="data" e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
              <div e-column e-field="ShipCity"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit"></div>
              <div e-column e-field="ShipCountry"></div>
          </div>
     </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
     
     syncApp.controller('EditingCtrl', function ($scope,$rootScope) {
         //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true ,showAddNewRow : true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 

{% endhighlight %}

The following output is displayed as a result of previous code example:

![](Editing_images/Editing_img27.png)


N> 1. If it is remote, then the newly added record is placed based on the index from current view data. 
N> 2. If it is local, then the newly added record is added at the top of the page even if the added new [`rowPosition`](http://help.syncfusion.com/api/js/ejgrid#members:editsettings-rowposition "rowPosition") is mentioned as "bottom".


## Default column values on add new

While adding new record in grid, there is an option to set the default value for the columns. Using [`e-defaultvalue`](http://help.syncfusion.com/api/js/ejgrid#members:columns-defaultvalue "defaultValue") property of [`columns`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns") you can set the default values for that particular column while editing or adding a new row.

The following code example describes the previous behavior.

{% highlight html %}
 <div ng-controller="EditingCtrl">
     <div id="Grid" ej-grid e-datasource="data"  e-allowpaging="true" e-editsettings="editSettings" e-toolbarsettings="toolbarItems">
          <div e-columns>
              <div e-column e-field="OrderID" e-isprimarykey="true"></div>
              <div e-column e-field="CustomerID"></div>
              <div e-column e-field="ShipCity" e-defaultvalue="Bern"></div>
			  <div e-column e-field="Freight" e-edittype="numericedit" e-defaultvalue="45"></div>
              <div e-column e-field="ShipCountry" e-defaultvalue="Brazil"></div>
          </div>
       </div>
 </div>
{% endhighlight %}

{% highlight javascript %}
    syncApp.controller('EditingCtrl', function ($scope,$rootScope) {
         //The datasource "window.gridData" is referred from 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js'
          $scope.data = window.gridData;
          $scope.editSettings = { allowEditing: true, allowAdding: true, allowDeleting: true};
          $scope.toolbarItems = { showToolbar: true, toolbarItems: ["add", "edit", "delete", "update", "cancel"] }
     }); 
{% endhighlight %}


The following output is displayed as a result of previous code example.

![](Editing_images/Editing_img28.png)


