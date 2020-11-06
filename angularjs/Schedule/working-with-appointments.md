---
title: Working with appointments | Syncfusion
description: Working with Scheduler appointments and its related options like Recurrence.
platform: AngularJS
control: schedule
documentation: ug
keywords: appointments, recurrence, recurring appointment, resize, drag and drop, search, categorize, priority, occurrence, reminder, filter and CRUD 
---

# Working with Appointments

An appointment represents a certain time interval in a schedule cell depicting a plan made for the specified time interval. 

## Appointment Types

The types of appointments available within Scheduler can be categorized as follows 

### Normal 

Represents an appointment that is created for a certain time interval in one or more number of days. If the normal appointment is created for more than 24 hours, then those longer appointments will be rendered on the all-day row.

N> If the normal appointment is to be created for two days (say from November 25, 2015 – 11.00 PM to November 26, 2015 2.00 AM) but less than 24 hour time interval, then the appointment is split into two partitions and will be displayed appropriately on both the days.

### All-Day 

Represents an appointment that is created for an entire day such as holiday events. It renders separately in an All-day row, a separate place for all-day appointments. In Timeline (horizontal) view, all-day appointment renders in the usual work cells, as no all-day cells are present in that view. 

N> An all-day row is normally visible on the Scheduler, as the `e-showalldayrow` property is set to true by default. 

### Recurrence

Represents an appointment that is created for a certain time interval that occurs repeatedly in a daily, weekly, monthly, yearly or every weekday basis at the same time interval based on the recurrence rule. The other available options and validations that can be performed on recurrence appointments can be referred from [here](/angularjs/schedule/working-with-appointments#recurrence-options).

## CRUD operation 

Appointments play a dynamic role within the Schedule control with which the users mostly interact. You can manipulate (add/edit/delete/drag/resize) the required appointments that reveals one of the main purpose of the Schedule control.

### Add/Edit Appointments

The appointments can be added/edited in the Scheduler using any one of the following ways,

* Quick window
* Inline creation/editing
* Default appointment window
* [Context menu](/angularjs/schedule/context-menu)
* Through programmatically

#### Quick Window

The Quick window usually pops out while single clicking on the Scheduler cells or appointments. It requires the user to enter the Subject to proceed with the appointment creation. It also includes an **Edit** **Appointment** option displayed at the bottom left corner – on selection which opens up the normal appointment window.

On single clicking the scheduler appointments, the pop-up that shows up contains the appointment information along with the other options that are listed below,

* Edit Appointment
* Edit Series (only for the recurrence appointments)
* Delete icon

The quick window option can be enabled/disabled by using `e-showquickwindow` API, whereas its default value is set to **true**.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-showquickwindow="false">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

N> Select multiple cells either using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>enter</kbd> key, so that the quick window opens up for the selected date/time range.

Another way to disable the quick window option at dynamic time can be achieved through the `e-cellclick` and `e-appointmentclick` events. The below code example shows the way to disable the quick appointment window only while clicking on the cells, but displays for appointments.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-showquickwindow="true" e-cellclick="onCellClick">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onCellClick = function(args) {
            args.cancel = true; // Prevents the display of quick window on clicking the cells.
        }
    </script>
</body>
</html>

{% endhighlight %}


#### Inline Appointment Creation/Editing

Another easier way, for adding or editing the appointment’s subject alone can be achieved using inline Add/Edit support. It allows the user to add and edit the appointments inline.

To get familiar with inline Add mode, single click on any of the Scheduler cells or press `enter` key on the selected cells. When the inline adding mode is ON, a text box will get created within the clicked Scheduler cells with a blinking cursor in it, requiring the user to enter the subject of an appointment. Once the subject is entered, the appointment will be saved on pressing the `enter` key. 

To enable inline edit mode, single click on any of the existing appointment’s subject, so that the user can edit the subject of that appointment. The edited subject of that appointment is then updated on pressing the `enter` key.

The inline option can be enabled/disabled on Scheduler by using the `e-allowinline` API, whereas its default value is set to **false**.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-allowinline="true">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

##### Enabling Inline Edit alone

It is possible to disable the inline appointment creation and enabling only the editing mode of inline by making use of the `e-cellclick` event. The below code example shows the way to disable the inline appointment creation while clicking on the cells, but appointments can be edited while clicking on it’s subject.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-showquickwindow="true" e-cellclick="onCellClick">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onCellClick = function(args) {
            args.cancel = true; // Prevents inline appointment creation on clicking the cells.
        }
    </script>
</body>
</html>

{% endhighlight %}


#### Default Appointment Window

The default appointment window is availed with options like 

* Subject
* Start and End Time
* All-Day
* TimeZone (for both Start and End time)
* Repeat options
* Description

The other additional options available are listed below for which the appropriate API’s are needed to be configured to display these options on the appointment window.

* Location ([showLocationField](/angularjs/schedule/miscellaneous#showhide-location-field))
* Priority ([prioritySettings](/angularjs/schedule/working-with-appointments#priority))
* Categorize ([categorizeSettings](/angularjs/schedule/working-with-appointments#categorization))
* [Resources](/angularjs/schedule/resources)    

The appointments can be created by double-clicking the Scheduler cells across the required time slots, which makes the Create Appointment window to pop-up. The start and end time fields will get automatically populated, according to the time-slot selection. Clicking on the done button in an appointment window will create the appointment for the selected time cells.

N> Select multiple cells both using mouse or keyboard access keys (<kbd>shift</kbd>+<kbd>arrow keys</kbd>) and press <kbd>Alt</kbd>+<kbd>N</kbd> key, so that the default appointment window opens up for the selected date/time range with the Start and End time fields automatically filled in.

To prevent the display of default appointment window on double clicking the Scheduler cells, either the `e-appointmentwindowopen` or `e-celldoubleclick` event can be used, within which the **args.cancel** needs to be set to true. This behavior is depicted in the below code example.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentwindowopen="onAppointmentWindowOpen">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onAppointmentWindowOpen = function(args) {
            args.cancel = true; // prevents the display of default appointment window
        }
    </script>
</body>
</html>
	
</script>

{% endhighlight %}

#### Through Programmatically

You can add/edit the appointments dynamically through the public method `saveAppointment`. It accepts the JSON Object data (either a new or updated appointment object) as its argument.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <button id="btnAdd" value="Add" onclick="addAppointment()">Add</button>
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        //addAppointment is a function, gets called on clicking the Add button
        function addAppointment() {
            //appointment details 
            var appointment = {
                Subject: "Gym",
                StartTime: new Date(2017, 1, 7, 4, 30),
                EndTime: new Date(2017, 1, 7, 5, 30)
            };

            //create the schedule object 
            var schObj = angular.element("#Schedule1").data("ejSchedule");
            //pass the JSON object in the public method 
            schObj.saveAppointment(appointment);
        }
    </script>
</body>
</html>

{% endhighlight %}

### Delete Appointments

The appointments can be deleted in either of the following ways,

* Selecting an appointment and clicking the delete icon in the quick appointment window.
* Hovering the mouse over appointments and clicking on Inline delete option which is enabled by default for all the appointments.
* Selecting an appointment and pressing <kbd>Delete</kbd> key.
* Through Programmatically.

A pop-up with a confirmation message will get displayed before deleting an appointment, which can be either switched on/off using the API `e-showdeleteconfirmationdialog`. Also, the confirmation text in that pop-up can be customized as mentioned [here](/angularjs/schedule/globalization-and-localization#localization:localizing-specific-words).

**For example**, to localize only the delete confirmation message in the delete window - 

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-showdeleteconfirmationdialog="true">
        </ej-schedule>
    </div>
    <script>
        var deleteCustomizationMessage = {
            // customize the confirmation message
            DeleteConfirmation: "Do you want to delete this Event?",
            // customize the delete window title
            MouseOverDeleteTitle: "Delete Event",
            // customize the recurrence delete window title
            RecurrenceDeleteTitle: "Delete Repeat Event"
        };

        // Extend only the required changes to the original locale collection
        $.extend(ej.Schedule.Locale["en-US"], deleteCustomizationMessage);

        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 10, 0),
                EndTime: new Date(2017, 1, 7, 11, 0)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

N> All these CRUD operations on appointments (add/edit/delete) can also be done through the default [context menu](/angularjs/schedule/context-menu#default-menu-options) options **Add Appointment**, **Edit Appointment** and **Delete Appointment** which is available, when context menu settings is enabled within Scheduler.

#### Through Programmatically

You can delete the appointments dynamically using the method `deleteAppointment`, which accepts the Guid of the appointment or complete appointment data as its argument. The Guid is availed as one of the appointment element’s attribute.

#### Example 1 - Using GUID 

The below code example depicts the way to delete the appointments using GUID programmatically by calling the **deleteAppointment** function within the `e-appointmentclick` event, which triggers whenever the user clicks on an appointment.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentclick="onAppointmentClick">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onAppointmentClick = function(args) {
            var schObj = angular.element("#Schedule1").data("ejSchedule");
            schObj.deleteAppointment(args.appointment.Guid);
            // angular.element(angular.element(".e-appointment")[0]).attr("data-guid") --> To get the guid attribute value of an element directly.
        }
    </script>
</body>
</html>

{% endhighlight %}

#### Example 2 - Using Appointment object 

The below code example depicts the way to delete the appointments using appointment data programmatically by calling the **deleteAppointment** function within the `e-appointmentclick` event, which triggers whenever the user clicks on an appointment.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentclick="onAppointmentClick">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onAppointmentClick = function(args) {
            var schObj = angular.element("#Schedule1").data("ejSchedule");
            schObj.deleteAppointment(args.appointment);
        }
    </script>
</body>
</html>

{% endhighlight %}

## Handling Appointment Actions

It is possible to define some specific actions to take place before the CRUD operation occurs on the Scheduler appointments through the following available client-side events,

* `e-beforeappointmentcreate`
* `e-beforeappointmentchange`
* `e-beforeappointmentremove`

**beforeAppointmentCreate** – Triggers before saving a new appointment.

**beforeAppointmentChange** – Triggers when an appointment is edited and before it is being updated to the dataSource.

**beforeAppointmentRemove** – Triggers before deleting an existing appointment.

To stop the save, edit and delete actions on the Scheduler appointments, following code example can be used.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-beforeappointmentcreate="onAppointmentSave" e-beforeappointmentchange="onAppointmentEdit" e-beforeappointmentremove="onAppointmentDelete">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onAppointmentSave = function(args) {
            args.cancel = true; // cancels the save action on appointments.
        }

        $scope.onAppointmentEdit = function(args) {
            args.cancel = true; // cancels the edit action on appointments.
        }

        $scope.onAppointmentDelete = function(args) {
            args.cancel = true; // cancels the delete action on appointments.
        }
    </script>
</body>
</html>

{% endhighlight %}

## Read Only

An interaction with the appointments of the Scheduler can be enabled/disabled through the `e-readonly` property. When the `e-readonly` property is set to `true`, it is not possible to do any actions on the appointments, but you can navigate between the schedule dates, views and can also be able to see the appointment details in the quick window. By default, this property is set to `false`.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-readonly="true">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

N> When the `e-readonly` property is set to true – double clicking the cells will open the appointment window filled with appointment details, which can be allowed to view but cannot be edited or saved.

## Drag and Drop

The appointment time can be modified through the drag and drop behavior, by dragging and dropping it to the new location, so that the start time and end time of the appointment gets changed automatically. We can enable/disable the drag and drop functionality through the `e-allowdraganddrop` property. By default, it is set to `true`.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-allowdraganddrop="false">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Handling Drag Actions Dynamically

The drag and drop functionality can be handled with the following three events,

* `e-dragstart`
* `e-drag`
* `e-dragstop`

**dragStart** – Triggers when the appointments are started to drag from its source location.

**drag** – Triggers when the appointments are being dragged over.

**dragStop** – Triggers when the appointments are dropped on a destined location.

The following code example shows how to cancel the dragging functionality with the help of one of these events.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-dragstop="onDragStop">
        </ej-schedule>
    </div>
    <script>
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onDragStop = function(args) {
            args.cancel = true; // cancels the drag action on appointments.
        }
    </script>
</body>
</html>

{% endhighlight %}

### External Drag and Drop

It is possible to drag and drop the external items to and fro the Scheduler control. This action is handled through the property `e-appointmentdragarea`, 
which specifies the draggable area name stating whether the appointments can be dragged outside of the control or within it.

The following code example lets you drag and drop the external items from the tree view control to the Scheduler.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <!-- Treeview List -->
        <div class="col-md-2">
            <span class=""><b>Tutorials </b></span>
            <div id="treeView" ej-treeview e-nodedragstart="onDragStart" e-nodeDropped="onDropped" e-allowdraganddrop=true width="170px" allowdropchild=false allowdropsibiling=false allowdraganddropaccesscontrol=true e-fields-datasource="dataList" e-fields-id="id" e-fields-parentid="parentId" e-fields-text="name" e-fields-haschild="hasChild" e-fields-expanded="expanded" />
        </div>
        <div class="col-md-9" style="float: left">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-cellwidth="40px" e-showcurrenttimeindicator="false" e-orientation="horizontal" e-views="scheduleViews" e-currentview="workweek" e-appointmentsettings-datasource="appointments"
            e-appointmentsettings-id="Id" e-appointmentsettings-subject="Subject" e-appointmentsettings-starttime="StartTime" e-appointmentsettings-endtime="EndTime" e-appointmentsettings-description="Description" e-appointmentsettings-allday="AllDay" e-appointmentsettings-recurrence="Recurrence" e-appointmentsettings-recurrencerule="RecurrenceRule" e-appointmentsettings-resourcefields="ownerId"
            e-group="group">
                    <e-resources>
                        <e-resource e-allowmultiple="true" e-field="ownerId" e-title="Owner" e-name="Owners" e-resourcesettings="resourcedata"></e-resource>                        
                     </e-resources>
        </ej-schedule>
        </div>
<div id="customWindow" style="display: none">
            <form id="custom">
                <table width="100%" cellpadding="5">
                    <tbody>
                        <tr>
                            <td>Subject:</td>
                            <td colspan="2">
                                <input id="subject" type="text" value="" name="Subject" style="width: 100%" readonly />
                            </td>
                        </tr>
                        <tr>
                            <td>Description:</td>
                            <td colspan="2">
                                <textarea id="customDescription" name="Description" rows="3" cols="50" style="width: 100%; resize: vertical"></textarea>
                            </td>
                        </tr>
                        <tr>
                            <td>StartTime:</td>
                            <td>
                                <input id="StartTime" type="text" ej-datetimepicker e-width="150px" />
                            </td>
                        </tr>
                        <tr>
                            <td>EndTime:</td>
                            <td>
                                <input id="EndTime" type="text" ej-datetimepicker e-width="150px" />
                            </td>
                        </tr>
                        <tr>
                            <td>Resource:</td>
                            <td colspan="2">
                                <input id="resource" type="text" value="" name="Resource" style="width: 100%" readonly />
                            </td>
                        </tr>
                        <tr style="display: none">
                            <td>ownerId:</td>
                            <td colspan="2">
                                <input id="ownerId" type="text" name="ownerId" />
                            </td>
                        </tr>
                    </tbody>
                </table>
            </form>
            <div>
                <button type="submit" onclick="cancel()" id="btncancel" ej-button e-width="85px" style="float: right; margin-right: 20px; margin-bottom: 10px;">Cancel</button>
                <button type="submit" onclick="save()" id="btnsubmit" ej-button e-width="85px" style="float: right; margin-right: 20px; margin-bottom: 10px;">Save</button>
            </div>
        </div>
</div>
<script type="text/javascript">
        angular.element(function () {
            angular.element("#customWindow").ejDialog({
                width: 600,
                height: "auto",
                showOnInit: false,
                enableModal: true,
                title: "Create Appointment",
                enableResize: false,
                allowKeyboardNavigation: false,
                close: "clearFields",
            });
            angular.element("#StartTime,#EndTime").ejDateTimePicker({ width: "150px" });
        });
        var TreeList = [
               { id: 1, name: "HTML", hasChild: true, expanded: true },
               { id: 2, parentId: 1, name: "Introduction" },
               { id: 3, parentId: 1, name: "Styles" },
               { id: 4, parentId: 1, name: "Editors" },
               { id: 5, parentId: 1, name: "Formatting " },
               { id: 6, name: "CSS", hasChild: true, expanded: true },
               { id: 7, parentId: 6, name: "Introduction" },
               { id: 8, parentId: 6, name: "Syntax" },
               { id: 9, parentId: 6, name: "Tables" },
               { id: 10, parentId: 6, name: "Box Model" },
               { id: 11, name: "JavaScript", hasChild: true },
               { id: 12, parentId: 11, name: "Introduction" },
               { id: 13, parentId: 11, name: "Data Types" },
               { id: 14, parentId: 11, name: "Variables" },
               { id: 15, name: "SQL", hasChild: true },
               { id: 16, parentId: 15, name: "Introduction" },
               { id: 17, parentId: 15, name: "Primary Key" },
               { id: 18, parentId: 15, name: "Distinct" },
               { id: 19, parentId: 15, name: "Ordered by" },
               { id: 20, parentId: 15, name: "Distinct" }];
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.dataList = TreeList;
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30),
                ownerId: 3
            }];
            $scope.setDate = new Date(2017, 1, 7);
            $scope.scheduleViews = ["Day", "Week", "WorkWeek", "Month"];
            $scope.group = {
                resources: ["Owners"]
            };
            $scope.resourcedata = {
                dataSource: [
                { text: "Nancy", id: 1, groupId: 1, color: "#f8a398" },
                { text: "Steven", id: 3, groupId: 2, color: "#56ca85" },
                { text: "Michael", id: 5, groupId: 1, color: "#51a0ed" },
                { text: "Milan", id: 13, groupId: 3, color: "#99ff99" },
                { text: "Paul", id: 15, groupId: 3, color: "#cc99ff" }
                ],
                text: "text", id: "id", groupId: "groupId", color: "color"
            };
            $scope.save = function () {
                var obj = {};
                var formelement = angular.element("#customWindow").find("#custom").get(0);
                for (var index = 0; index < formelement.length; index++) {
                    var columnName = formelement[index].name, $element = angular.element(formelement[index]);
                    if (columnName != undefined) {
                        if (columnName == "Subject")
                            var value = formelement[index].value;
                        if (columnName == "Description")
                            value = formelement[index].value;
                        if ($element.hasClass("e-datetimepicker")) {
                            columnName = $element.attr("id");
                            value = new Date(formelement[index].value);
                        }
                        if (columnName == "ownerId")
                            value = parseInt(formelement[index].value);
                        if (columnName != "Resource")
                            obj[columnName] = value;
                    }
                }
                angular.element("#customWindow").ejDialog("close");
                var object = angular.element("#Schedule1").data("ejSchedule");
                object.saveAppointment(obj);
            }
            $scope.cancel = function () {
                angular.element("#customWindow").ejDialog("close");
            }
            $scope.onDragStart = function (e) {
                if (e.targetElementData.parentId == "") return false;
            }
            $scope.onDropped = function (e) {
                if (angular.element(e.target).parents(".e-schedule").length != 0) {
                    var scheduleObj = angular.element("#Schedule1").data("ejSchedule");
                    var result = scheduleObj.getSlotByElement($(e.target));
                    // set value to custom appointment window fields
                    angular.element("#subject").val(e.droppedElementData.text);
                    angular.element("#customDescription").val(e.droppedElementData.text);
                    angular.element("#StartTime").ejDateTimePicker({ value: new Date(result.startTime) });
                    angular.element("#EndTime").ejDateTimePicker({ value: new Date(result.endTime) });
                    angular.element("#resource").val(result.resources.text);
                    angular.element("#ownerId").val(result.resources.id);
                    angular.element("#customWindow").ejDialog("open");
                }
            }
        });
    </script>
</body>
</html>

{% endhighlight %}

## Resize

Resizing an appointment is another way to change its start and end time. Mouse hover on the appointments, so that the resizing handlers gets displayed on either sides of the appointment which allows resizing. The resizing functionality can be enabled/disabled by setting the `e-enableappointmentresize` property. By default it is set to `true`.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-enableappointmentresize="false">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30),
                ownerId: 3
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Handling Resize Actions Dynamically

The appointment resizing functionality can be handled through the following three events,

* `e-resizestart`
* `e-resize`
* `e-resizestop`

**resizeStart** – Triggers when the appointments are started resizing from its original time.

**resize** – Triggers when the appointment resizing is in progress.

**resizeStop** – Triggers when the appointment resizing is done.

The following code example shows how to cancel the resizing functionality with the help of one of these events.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-resizestart="onResizeStart">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Talk with Nature",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30),
                ownerId: 3
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
        $scope.onResizeStart = function(args) {
            args.cancel = true; // Blocks the resize action on appointments.
        }
    </script>
</body>
</html>

{% endhighlight %}

## Categorization

It allows to differentiate the appointments with various categorize options and individual colors. You can also denote the status of the appointments using this categorize option and can specify your own user-defined category collection. It is also possible to select multiple categorize for a single appointment.

### Categorize Settings

The `e-categorizesettings` holds the below categorize related properties such as,

* `e-categorizesettings-enable` - It accepts true or false value, denoting whether to enable/disable the categorize option. Its default value is `false`.
* `e-categorizesettings-allowmultiple` – It enables or disables the multiple selection of categories for each appointments in the appointment window as well as in the context menu. Its default value is `false`.
* `e-categorizesettings-datasource` – Binds the categorize dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview). 

We have below 6 default values for Categorize dataSource collection.

{% highlight js %}

categorizeSettings: {
    dataSource: [{
        text: "Blue Category",
        id: 1,
        color: "#43b496",
        fontColor: "#ffffff"
    }, {
        text: "Green Category",
        id: 2,
        color: "#7f993e",
        fontColor: "#ffffff"
    }, {
        text: "Orange Category",
        id: 3,
        color: "#cc8638",
        fontColor: "#ffffff"
    }, {
        text: "Purple Category",
        id: 4,
        color: "#ab54a0",
        fontColor: "#ffffff"
    }, {
        text: "Red Category",
        id: 5,
        color: "#dd654e",
        fontColor: "#ffffff"
    }, {
        text: "Yellow Category",
        id: 6,
        color: "#d0af2b",
        fontColor: "#ffffff"
    }]
}

{% endhighlight %}

The below categorize fields holds the appropriate column names from the dataSource - 

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
id<br/><br/></td><td>
It holds the binding name for <b>id</b> field in the categorize dataSource<br/><br/></td></tr>
<tr>
<td>
text<br/><br/></td><td>
It holds the binding name for <b>text</b> field in the categorize dataSource<br/><br/></td></tr>
<tr>
<td>
color<br/><br/></td><td>
It holds the binding name for <b>color</b> field in the categorize dataSource.<br/><br/></td></tr>
<tr>
<td>
fontColor<br/><br/></td><td>
It holds the binding name for <b>fontColor</b> field in the categorize dataSource. This font color applies for the appointment.<br/><br/></td></tr>
</table>

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentsettings-categorize="Categorize"
            e-categorizesettings-enable="true" e-categorizesettings-allowmultiple="true" e-categorizesettings-datasource="categorizeDataSource" e-categorizesettings-text="text" e-categorizesettings-id="id" e-categorizesettings-color="color" e-categorizesettings-fontcolor="fontColor">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.categorizeDataSource = [{
                text: "Blue Category",
                id: 1,
                color: "#43b496",
                fontColor: "#ffffff"
            }, {
                text: "Green Category",
                id: 2,
                color: "#7f993e",
                fontColor: "#ffffff"
            }, {
                text: "Orange Category",
                id: 3,
                color: "#cc8638",
                fontColor: "#ffffff"
            }, {
                text: "Purple Category",
                id: 4,
                color: "#ab54a0",
                fontColor: "#ffffff"
            }, {
                text: "Red Category",
                id: 5,
                color: "#dd654e",
                fontColor: "#ffffff"
            }, {
                text: "Yellow Category",
                id: 6,
                color: "#d0af2b",
                fontColor: "#ffffff"
            }];
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30),
                Categorize: "3",
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30),
                Categorize: "1,2,6" // Multiple categorize id passing 
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

## Priority

This option prioritize the appointments based on its importance and it can be differentiated with each individual icons/images. By default, there are some specific set of default priority collection and you can also customize it with your own priority collection.

### Priority Settings

The prioritySettings holds the below priority related properties such as,

* `e-prioritysettings-enable` - It accepts true or false value, denoting whether to enable/disable the priority option. Its default value is **false**.
* `e-prioritysettings-template` – Customize the priority icon/images using template options.
* `e-prioritysettings-datasource` – binds the priority dataSource collection. This property should be assigned with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview). 

We have below 4 default values for priority dataSource collection.

{% highlight js %}

prioritySettings: {
    dataSource: [{
        text: "None",
        value: "none"
    }, {
        text: "High",
        value: "high"
    }, {
        text: "Medium",
        value: "medium"
    }, {
        text: "Low",
        value: "low"
    }]
}

{% endhighlight %}

The below priority fields holds the appropriate column names from the dataSource,

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
text<br/><br/></td><td>
It holds the binding name for <b>text</b> field in the priority dataSource<br/><br/></td></tr>
<tr>
<td>
value<br/><br/></td><td>
It holds the binding name for <b>value</b> field in the priority dataSource.<br/><br/></td></tr>
</table>

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentsettings-priority="priority"
            e-prioritysettings-enable="true" e-prioritysettings-datasource="priorityDataSource" e-prioritysettings-text="text" e-prioritysettings-value="value">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.priorityDataSource = [{
                text: "None",
                value: "none"
            }, {
                text: "High",
                value: "high"
            }, {
                text: "Low",
                value: "low"
            }];
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30),
                priority: "low", //pass the priority value
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30),
                priority: "high" //pass the priority value
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

## Search or Filter Appointments

### Appointment Search

The public method `searchAppointments` is used to search the appointments in the Scheduler dataSource. It contains the below four arguments such as search string, search field, filter operator and ignore case.

**searchString** - It is used to search the given word/sentence within the appointment data.

**fields** - It is the field with which the search operation takes place. It’s an optional argument.

**filterOperator** – It denotes the filter type like `contains`, `greaterthan` or `lessthan`. It’s an optional argument.

**ignoreCase** – It is a boolean value to set the search string as case sensitive or not. It’s an optional argument.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <input id="txtSearch" type="text" />
        <input id="btnSearch" class="searchApp" ej-button e-click="searchAppointments" type="button" value="Search" />
        <div id="grid1"></div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
            $scope.searchAppointments = function () {
                var _searchString = angular.element("#txtSearch").val();
                var schObj = angular.element("#Schedule1").data("ejSchedule");
                // method to retrieve the appointment based on search string
                var result = schObj.searchAppointments(_searchString);
                showResult(result, _searchString);
            }
            // method to show the result in a grid
            function showResult(list, _searchString) {
                if (!ej.isNullOrUndefined(list) && list.length != 0 && _searchString != "") {
                    angular.element("#grid1").show();
                    angular.element("#grid1").data("ejGrid") && angular.element("#grid1").ejGrid("destroy");
                    angular.element("#grid1").ejGrid({
                        allowScrolling: true,
                        dataSource: list,
                        allowPaging: true
                    });
                }
            }
        });
    </script>
</body>
</html>

{% endhighlight %}

### Appointment Filters

The appointments can be filtered or shortlisted based on the simple or complex conditions with four available properties such as **field**, **operator**, **value** and **predicate** which is passed to the public method `filterAppointments`.

**field** - It is the field, with which the search operation takes place. It’s an optional argument.

**operator** – It is generally used to specify the [filter](/angularjs/datamanager/filtering) type. 

**value** – It is the filter keyword based on which the records are filtered.

**predicate** – To add more than one conditional query, need to use `and`, `or` [predicates](/angularjs/datamanager/filtering#and-predicate).

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <input id="btnSearch" class="filterApp" ej-button e-click="filterAppointments" type="button" value="Filter" />
        <div id="grid1"></div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 7, 9, 0),
                EndTime: new Date(2017, 1, 7, 14, 30)
            }];
            $scope.setDate = new Date(2017, 1, 7);
            $scope.filterAppointments = function () {
                // Add the filter data as like in the below format
                var filter = [{
                    field: "Subject", // field configure
                    operator: "contains",
                    value: "Music",
                    predicate: "or" // predicate 
                }, {
                    field: "Subject", // field configure
                    operator: "contains",
                    value: "School",
                    predicate: "or" // predicate
                }];

                var schObj = angular.element("#Schedule1").data("ejSchedule");
                // Method to get the Filtered appointment
                var result = schObj.filterAppointments(filter);
                showResult(result);
            }
            // method to show the result in a grid
            function showResult(list) {
                if (!ej.isNullOrUndefined(list) && list.length != 0) {
                    angular.element("#grid1").show();
                    angular.element("#grid1").data("ejGrid") && angular.element("#grid1").ejGrid("destroy");
                    angular.element("#grid1").ejGrid({
                        allowScrolling: true,
                        dataSource: list,
                        allowPaging: true
                    });
                }
            }
        });
    </script>
</body>
</html>

{% endhighlight %}


## Recurrence Options

There are scenarios where you require the same appointments to be repeatedly created for multiple days on daily, weekly, monthly, and yearly or on every weekday basis. 

In appointment data collection, **recurrence** and **recurrenceRule** are dependent fields. While creating or binding the recurrence appointment, the **recurrence** field is set to **true** and **recurrenceRule** contains recurrence pattern in string format.

### Recurrence Rule

The recurrence appointments are created based on the recurrence rule. The RecurrenceRule is a string value that contains the details of the recurrence appointments like 

* repeat type - daily/weekly/monthly/yearly/every weekday 
* how many times it needs to be repeated 
* the interval duration
* the time period to render the appointment, etc.,

It has the following properties based on which the recurrence appointments are rendered in the Schedule control with its respective time period.

<table>
<tr>
<th>
S.No<br/><br/></th><th>
Property<br/><br/></th><th>
Purpose<br/><br/></th></tr>
<tr>
<td>
1<br/><br/></td><td>
FREQ<br/><br/></td><td>
Maintains the Repeat type value of the appointment. <br/><br/>(<b>Example</b>: Daily, Weekly, Monthly, Yearly, Every week day)<br/><br/>Example: <b>FREQ=DAILY</b>;INTERVAL=1<br/><br/></td></tr>
<tr>
<td>
2<br/><br/></td><td>
INTERVAL<br/><br/></td><td>
Maintains the interval value of the appointments.<br/><br/><b>For example</b>, when you create the daily appointment at an interval of 2, the appointments are rendered on the days Monday, Wednesday and Friday. (Creates an appointment on all days by leaving the interval of one day gap)<br/><br/>Example: FREQ=DAILY;<b>INTERVAL=2</b><br/><br/></td></tr>
<tr>
<td>
3<br/><br/></td><td>
COUNT<br/><br/></td><td>
It holds the appointment’s count value. <br/><br/><b>For example</b>, When the recurrence appointment count value is 10, which means that 10 instances of appointments are created in the recurrence series.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>COUNT=10</b><br/><br/></td></tr>
<tr>
<td>
4<br/><br/></td><td>
UNTIL<br/><br/></td><td>
This property is used to store the recurrence end date value. <br/><br/><b>For example</b>, when you set the end date of appointment as 11/30/2015, the UNTIL property holds the end date value denoting when the recurrence actually ends.<br/><br/>Example: FREQ=DAILY;INTERVAL=1;<b>UNTIL=11/30/2015</b><br/><br/></td></tr>
<tr>
<td>
5<br/><br/></td><td>
BYDAY<br/><br/></td><td>
It holds the <b>DAY</b> values, representing on which the appointments actually renders. <br/><br/><b>For example</b>, Create the weekly appointment, and select the day(s) from the day options (Monday/Tuesday/Wednesday/Thursday/Friday/Saturday/Sunday). When Monday is selected, the first two letters of the selected day “MO” is saved in the <b>BYDAY</b> property. When multiple days are selected, the values are separated by commas.<br/><br/>Example: FREQ=WEEKLY;INTERVAL=1;<b>BYDAY=MO,WE</b>;COUNT=10<br/><br/></td></tr>
<tr>
<td>
6<br/><br/></td><td>
BYMONTHDAY<br/><br/></td><td>
This property is used to store the date value of the Month, while creating the Month recurrence appointment.<br/><br/><b>For example</b>, when you create a Monthly recurrence appointment for every 3rd day of the month, then <b>BYMONTHDAY</b> holds the value 3 and creates the appointment on 3rd day of every month.<br/><br/>Example: FREQ=MONTHLY;<b>BYMONTHDAY=3</b>;INTERVAL=1;COUNT=10<br/><br/></td></tr>
<tr>
<td>
7<br/><br/></td><td>
BYMONTH<br/><br/></td><td>
This property is used to store the index value of the selected Month while creating the yearly appointments.<br/><br/><b>For example</b>, when you create the yearly appointment on June month, the index value of June month 6 will get stored in the BYMONTH field. The appointment is created on every 6th month of a year.<br/><br/>Example: FREQ=YEARLY;BYMONTHDAY=16;<b>BYMONTH=6</b>;INTERVAL=1;COUNT=10<br/><br/></td></tr>
<tr>
<td>
8<br/><br/></td><td>
BYSETPOS<br/><br/></td><td>
This property is used to store the index value of the week. <br/><br/><b>For example</b>, when you create the monthly appointment in second week of a month, the index value of the second week (2) is stored in BYSETPOS.<br/><br/>Example: FREQ=MONTHLY;BYDAY=MO;<b>BYSETPOS=2</b>;UNTIL=8/11/2015<br/><br/></td></tr>
<tr>
<td>
9<br/><br/></td><td>
WKST<br/><br/></td><td>
This property is used to store the start day value of a week.<br/><br/><b>For example</b>, when you render the workweek the “WKST” value is Monday.<br/><br/></td></tr>
<tr>
<td>
10 <br/><br/></td><td>
EXDATE<br/><br/></td><td>
EXDATE is used to hold the modified appointment date details (date value) in the recurrence appointment series.<br/><br/><b>For example</b>, when you change the recurrence appointment instance under the date “6/19/2015”, then this date is added to the recurrence rule EXDATE field. “EXDATE” is also used to differentiate the edited occurrence of the recurrence series for some internal process while doing the “Edit Series or Delete series” actions.<br/><br/>Example: FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;<b>EXDATE=6/18/2015,6/20/2015</b>;RECUREDITID=1651<br/><br/></td></tr>
<tr>
<td>
11<br/><br/></td><td>
RECUREDITID<br/><br/></td><td>
This property contains the Parent Id value of the edited appointment. It is used to track the edited appointment occurrence with its parent recurrence appointment series.<br/><br/><b>For example</b>, when you edit the particular occurrence of the recurrence appointment series, the “RECUREDITID” is added to that edited appointment depicting its parent Id.<br/><br/>Example:<br/><br/>FREQ=WEEKLY;BYDAY=MO,TU,WE,TH,FR;COUNT=10;EXDATE=6/18/2015,6/20/2015;<b>RECUREDITID=1651</b><br/><br/></td></tr>
</table>
To know more about other possible combinations of above specified recurrence rule properties, refer [here](http://www.syncfusion.com/kb/3719/what-is-recurrencerule-in-the-schedule-control).

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-appointmentsettings-datasource="appointments" e-appointmentsettings-recurrence="Recurrence" e-appointmentsettings-recurrencerule="RecurrenceRule">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 6, 9, 0),
                EndTime: new Date(2017, 1, 6, 14, 30),
                Recurrence: true, //enable recurrence options
                RecurrenceRule: "FREQ=DAILY;INTERVAL=1;COUNT=5" //Recurrence rule.
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Recurrence Validation

The default recurrence validation has been included for recurrence appointments similar to the one available in outlook. The validation occurs during the recurrence appointment creation, drag and drop or resizing of the recurrence appointments and also if any single occurrence changes. The validation can be disabled by setting the `e-enablerecurrencevalidation` property to `false`.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate" e-enablerecurrencevalidation="false" e-appointmentsettings-datasource="appointments" e-appointmentsettings-recurrence="Recurrence" e-appointmentsettings-recurrencerule="RecurrenceRule">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(2017, 1, 7, 6, 0),
                EndTime: new Date(2017, 1, 7, 7, 30)
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(2017, 1, 6, 9, 0),
                EndTime: new Date(2017, 1, 6, 14, 30),
                Recurrence: true, //enable recurrence options
                RecurrenceRule: "FREQ=DAILY;INTERVAL=1;COUNT=5" //Recurrence rule.
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

N> You can parse the **RecurrenceRule** of an appointment from the server-side by making use of a new generic utility class **RecurrenceHelper**. Refer this [KB document](https://www.syncfusion.com/kb/5390/how-to-parse-the-recurrencerule-in-server-side).

### Recurrence Edit and Delete options

The recurring appointments can be edited or deleted in three ways as below:

* Single occurrence
* Following appointments
* Entire series

#### Single occurrence

When an option "Only this Appointment" is selected, a single occurrence of the recurrence appointment alone will be edited or deleted.

#### Following appointments

When an option "Following Appointments" is selected, all the following events of the recurrence appointment from the current instance will be edited or deleted. The previous instances of the recurrence appointment before this current instances will be retained as it is on the Scheduler.

#### Entire series

The entire recurrence series will be edited / deleted, on selecting this option.

## Reminder

Reminder option notifies all the appointments before some specific time. By default, it notifies before 5 minutes. Each and every appointment triggers the `e-reminder` event and can utilize this event for other user actions like mailing particular event to someone or to do any kind of manipulations with the reminder appointments and so on. The `reminderSettings` includes the following 2 properties namely,

* **e-remindersettings-enable** - To enable the reminder settings of the Schedule control, set the **enable** property as `true` within the `e-reminderSettings` option.

* **e-remindersettings-alertbefore** - Accepts the integer value to denote the time, before how long the reminder should be notified to the user.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-remindersettings-enable="true" e-remindersettings-alertbefore="10" e-reminder="reminderCustom" e-timezone="UTC +00:00" e-appointmentsettings-datasource="appointments">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            $scope.appointments = [{
                Id: 1,
                Subject: "Music Class",
                StartTime: new Date(new Date().setMinutes(new Date().getMinutes() + 11)),
                EndTime: new Date(new Date().setHours(new Date().getHours() + 1))
            }, {
                Id: 2,
                Subject: "School",
                StartTime: new Date(new Date().setHours(new Date().getHours() + 2)),
                EndTime: new Date(new Date().setHours(new Date().getHours() + 4))
            }];
        });
        $scope.reminderCustom = function(args) {
            alert("Reminder Appointment");
        }
    </script>
</body>
</html>

{% endhighlight %}

N> Whenever the reminder setting is enabled in the Scheduler with some specific value (in minutes) assigned to the **e-alertbefore** property, the **e-reminder** event gets triggered before this specified value. It includes the reminder appointment’s entire information within its arguments.

## Block Time Intervals

It allows to block the particular timeslots in Schedule. When specific timeslots are blocked, the appointments that lies in that range can either be made read-only or else can be allowed to interact with the users based on the value assigned to the `e-blockoutsettings-isblockappointment` property.

### Blockout Settings

The `blockoutSettings` holds the below block intervals related properties such as,

* `e-blockoutsettings-enable` - It accepts true or false value, denoting whether to enable/disable the block intervals option. It's default value is `false`.
* `e-blockoutsettings-templateid` - It applies the template design to block the intervals.
* `e-blockoutsettings-datasource` - Binds the block intervals dataSource collection. This property should be assigned either with the JSON data array collection or instance of [ej.DataManger](/js/datamanager/overview).

The below blockout fields holds the appropriate column names from the dataSource - 

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
id<br/><br/></td><td>
It holds the binding name for <b>id</b> field in the blockout dataSource<br/><br/></td></tr>
<tr>
<td>
subject<br/><br/></td><td>
It holds the binding name for <b>subject</b> field in the blockout dataSource<br/><br/></td></tr>
<tr>
<td>
startTime<br/><br/></td><td>
It holds the binding name for <b>startTime</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
endTime<br/><br/></td><td>
It holds the binding name for <b>endTime</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
isBlockAppointment<br/><br/></td><td>
It holds the binding name for <b>isBlockAppointment</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
isAllDay<br/><br/></td><td>
It holds the binding name for <b>isAllDay</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
resourceId<br/><br/></td><td>
It holds the binding name for <b>resourceId</b> field in the blockout dataSource.<br/><br/></td></tr>
<tr>
<td>
customStyle<br/><br/></td><td>
It holds the binding name for <b>customStyle</b> field in the blockout dataSource.<br/><br/></td></tr>
</table>

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate"
                     e-blockoutsettings-datasource="blockDataSource" e-blockoutsettings-enable="true" e-blockoutsettings-id="BlockId" e-blockoutsettings-starttime="BlockStartTime" e-blockoutsettings-endtime="BlockEndTime" e-blockoutsettings-subject="BlockSubject" e-blockoutsettings-isblockappointment="IsBlockAppointment">
        </ej-schedule
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            //data source block intervals
            $scope.blockDataSource = [{
                BlockId: 101,
                BlockStartTime: new Date(2017, 1, 7, 10, 00),
                BlockEndTime: new Date(2017, 1, 7, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true
            }, {
                BlockId: 102,
                BlockStartTime: new Date(2017, 1, 7, 12, 00),
                BlockEndTime: new Date(2017, 1, 7, 13, 00),
                BlockSubject: "Maintenance",
                IsBlockAppointment: true
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Blocking Appointments

The Appointments that lies within the blocked time range can be restricted to perform CRUD operations in it and can be made read-only. This can be achieved by setting `isBlockAppointment` property to true.


{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate"
                     e-blockoutsettings-datasource="blockDataSource" e-blockoutsettings-enable="true" e-blockoutsettings-id="BlockId" e-blockoutsettings-starttime="BlockStartTime" e-blockoutsettings-endtime="BlockEndTime" e-blockoutsettings-subject="BlockSubject" e-blockoutsettings-isblockappointment="IsBlockAppointment">
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            //data source block intervals
            $scope.blockDataSource = [{
                BlockId: 101,
                BlockStartTime: new Date(2017, 1, 7, 10, 00),
                BlockEndTime: new Date(2017, 1, 7, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true //block appointment field in datasource
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Customizing block time intervals

The `blockoutSettings` holds the below properties to customize the block intervals such as,

* `e-blockoutsettings-templateid` - Template design that applies on the block intervals.
* `e-blockoutsettings-customstyle` - The custom CSS that applies on the blocked intervals.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate"
            e-blockoutsettings-datasource="blockDataSource" e-blockoutsettings-enable="true" e-blockoutsettings-templateid="#blocktemplate" e-blockoutsettings-id="BlockId" e-blockoutsettings-starttime="BlockStartTime" e-blockoutsettings-endtime="BlockEndTime" e-blockoutsettings-subject="BlockSubject" e-blockoutsettings-isblockappointment="IsBlockAppointment">
        </ej-schedule>
    </div>
    <!--Template to apply block intervals-->
    <script id="blocktemplate" type="text/x-jsrender">
        <div style="height:100%;color:red;font-weight:bold;"><div>{{:BlockSubject}}</div></div>
    </script>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            //data source block intervals
            $scope.blockDataSource = [{
                BlockId: 101,
                BlockStartTime: new Date(2017, 1, 7, 10, 00),
                BlockEndTime: new Date(2017, 1, 7, 11, 00),
                BlockSubject: "Service",
                IsBlockAppointment: true //block appointment field in datasource
            }];
            $scope.setDate = new Date(2017, 1, 7);
        });
    </script>
</body>
</html>

{% endhighlight %}

### Blocking time interval based on resources

* `e-blockoutsettings-resourceid` - property used within the `blockoutSettings` which accepts the resource id's can be used to apply the block intervals based on the resources.

{% highlight html %}

<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml" ng-app="ScheduleApp">
<head>
    <!-- Dependency file references -->
</head>
<body>
    <div ng-controller="ScheduleCtrl">
        <ej-schedule id="Schedule1" e-width="100%" e-height="525px" e-currentdate="setDate"
            e-appointmentsettings-datasource="appointments" e-appointmentsettings-id="EventId" e-appointmentsettings-subject="EventSubject" e-appointmentsettings-starttime="EventStartTime" e-appointmentsettings-endtime="EventEndTime" e-appointmentsettings-resourcefields="ownerId"
            e-blockoutsettings-datasource="blockDataSource" e-blockoutsettings-enable="true" e-blockoutsettings-id="BlockId" e-blockoutsettings-starttime="BlockStartTime" e-blockoutsettings-endtime="BlockEndTime" e-blockoutsettings-subject="BlockSubject" e-blockoutsettings-isblockappointment="IsBlockAppointment" e-blockoutsettings-resourceid="BlockResId"
            e-group="group">
               <e-resources>
                   <e-resource e-allowmultiple="true" e-field="ownerId" e-title="Owner" e-name="Owners" e-resourcesettings="resourcedata"></e-resource>                        
               </e-resources>
        </ej-schedule>
    </div>
    <script type="text/javascript">
        angular.module('ScheduleApp', ['ejangular']).controller('ScheduleCtrl', function ($scope) {
            //data source for appointments
            $scope.appointments = [{
                EventId: 1,
                EventSubject: "Research on Sky Miracles",
                EventStartTime: new Date(2017, 1, 7, 9, 0),
                EventEndTime: new Date(2017, 1, 7, 10, 30),
                ownerId: 2
            }];
            //data source for block intervals
            $scope.blockDataSource = [{
                BlockId: 101,
                BlockStartTime: new Date(2017, 1, 7, 11, 00),
                BlockEndTime: new Date(2017, 1, 7, 12, 00),
                BlockSubject: "Travel",
                IsBlockAppointment: true,
                BlockResId: 2
            }];
            $scope.setDate = new Date(2017, 1, 7);
            $scope.group = {
                resources: ["Owners"]
            };
            $scope.resourcedata = {
                dataSource: [
                   { text: "Nancy", id: 1, color: "#f8a398" },
                   { text: "Steven", id: 2, color: "#56ca85" }
                ],
                text: "text", id: "id", color: "color"
            };
        });
    </script>
</body>
</html>

{% endhighlight %}

