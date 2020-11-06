---
layout: post
title: Getting-Started | Tab | JavaScript | Syncfusion
description: getting started 
platform: AngularJS
control: Tab
documentation: ug
keywords: ejtab, tab, angularjs tab 
---

# Getting Started 

This section explains briefly about how to create a **Tab** Control in your application with **JavaScript**. The **Essential JavaScript Tab** control is an interface that displays the content in multiple sections. Each **TabPanel** consists of **HeaderText** or **HeaderTemplate** as well as a **ContentTemplate**. **Tab** is useful for a dashboard that is having limited space. The following section guides you to on-demand customize the **Tab** for displaying Hotel menu items, its rating details and ingredients.

![](/js/Tab/Getting-Started_images/Getting-Started_img1.png) 

## Create Tab Control in AngularJS

**Essential JavaScript Tab** widget basically builds a dynamic interactive menu-driven interface from your content. The content can be text, graphics or HTML. You can create the **Tab** headers using &lt;UL&gt; and &lt;LI&gt; tags and content panels using &lt;div&gt; tags. 

Essential JS includes angular directives for all controls in the ej.widget.angular.min.js script file. All the Essential JS directives have been encapsulated into a single module called angular.min.js. To render our ej controls in angular, you need to refer the **“angular.min.js”** and **“ej.widget.angular.min.js”** in your application.

The following steps describe the creation of **Tab** control.  

Create an **HTML** file and add the following template in the HTML file for creating **Tab** control.

{% highlight html %}

<!doctype html>
<html lang="en" ng-app="tabApp">
<head>
    <title>Essential Studio for JavaScript : Angular JS Support for Tab </title>
    <!-- Style sheet for default theme (flat azure) -->
    <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
    <!--Scripts-->
    <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.11.3.min.js" type="text/javascript"> </script> 
    <script src="http://cdn.syncfusion.com/js/assets/external/angular.min.js"></script>
    <script type="text/javascript" src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js "></script>
    <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/common/ej.widget.angular.min.js"></script>
    <!--Add custom scripts here -->
</head>
<body ng-controller="TabCtrl">

<!--Add necessary HTML elements-->

</body>
</html>

{% endhighlight %}

The ng-app directive explains the root element (<html> or <body> tags) of the application. You will assign a name to the ng-app directive, then you must create a module with that name. In this module, you will have to define your directives, services, filters and configurations.

A controller is defined using ng-controller directive. Each controller accepts an object $scope which we pass as a parameter.  This object is used to bind the controller with view.   

Properties can be bind to ejTab control using the prefix e- and particular property name.

Add **Tab** header within &lt;body&gt; tag.

{% highlight html %}

    <div id="dishType" ej-tab style="width: 550px">
        <ul>
            <li><a href="#pizza">Pizza Menu</a></li>
            <li><a href="#sandwich">Sandwich Menu</a></li>
            <li><a href="#pasta">Pasta Menu</a></li>
        </ul>

{% endhighlight %}

Initialize **Tab** in &lt;script&gt; tag.

To render the ejTab using angular directive, we need to inject the ej angular directive with modules shown as below,

{% highlight js %}

    <script>
        angular.module('tabApp', ['ejangular'])
         .controller('TabCtrl', function ($scope) {
         });
    </script>

{% endhighlight %}

The following screen shot illustrates the **Tab** control with Header.

![](/js/Tab/Getting-Started_images/Getting-Started_img2.png) 

## Configure Content

In this application a detailed description is provided to each item. You can specify the contents in the **Tab** section within the &lt;div&gt; element. 

{% highlight html %}

<div id="pizza" style="background-color: #F5F5F5">
     <!--Food item description-->
     <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>
</div>

{% endhighlight %}

You can provide more customization to the **Tab** with **rating** control as content in it for describing the item rating value. 

## Create the Rating 

The **Essential JavaScript Rating** control provides you an intuitive rating experience that allows you to select the number of stars that represents the rating. For more information about the rating please refer the following link: 

<http://help.syncfusion.com/js/rating/getting-started>

The following code example explains you the **rating** control creation. The input element is used to create the **rating** control. Render the input element as **rating** control using the input element id. The code example can be placed within the content description &lt;div&gt; element to declare the rating control and description in the **Tab** section and it can be appended with the header initialization code section &lt;div&gt; element.

{% highlight html %}

div id="dishType" ej-tab style="width: 550px">
        <ul>
            <li><a href="#pizza">Pizza Menu</a></li>
            <li><a href="#sandwich">Sandwich Menu</a></li>
            <li><a href="#pasta">Pasta Menu</a></li>
        </ul>
        <div id="pizza" style="background-color: #F5F5F5">
            <p>Rating:</p>
            <!--Rating control declaration-->
            <div class="dishRating">
                <input id="pizzaRating" ej-rating type="text" class="rating" />
            </div>
            <!--Food item description-->
            <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>
        </div>
    </div>

{% endhighlight %}

To render the **rating** controls in the first **Tab** element refer the styles mentioned in the following code example.

{% highlight css %}

<style type="text/css" class="cssStyles">
    .dishRating {
        position: absolute;
        margin: -31px 0px 0px 80px;
    }        
</style>


{% endhighlight %}

The following code example is used for rendering the content with **rating** control within the first **Tab** content section.

{% highlight js %}

    <script>
        angular.module('tabApp', ['ejangular'])
         .controller('TabCtrl', function ($scope) {
         });
    </script>

{% endhighlight %}

The following screenshot illustrates the **Tab** content with rating control. 

![](/js/Tab/Getting-Started_images/Getting-Started_img3.png) 

## Ajax Content Load (Load On Demand) 

You can change the contents in sub **Tab** element periodically and you are provided with a support to change the contents without any problems. To achieve the content load, use the Load on Demand concept.

In Load On-Demand, the external HTML file with the necessary details is referred in &lt;href&gt; section during **Tab** header declaration section. When you click the **Tab** header, the Ajax automatically calls the content from the external files and displays in a **Tab** content section.

### Sub Tab with Ajax Content

Each item is having a variety of options and these options are also specified in the limited space. So you can choose the **Tab** control that is used within the root **Tab** to specify more details.

The following code example illustrates to create the **Tab** control within the root **Tab** element. This HTML code is appended within the previous HTML code section. To render the child **Tab** with its header, add this code example within the first **Tab** &lt;div&gt; element.

{% highlight html %}

<!--sub Tab control, the contents loaded with load on demand-->
  <div id="pizzaType" ej-tab>
                <ul>
                    <li><span class="cornSpinach"></span>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/cornSpainach.html">Corn & Spinach </a></li>
                    <li><span class="chickenDelite"></span>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/ChickenDelite.html">Chicken Delite </a></li>
                </ul>
   </div>


{% endhighlight %}

The Load On-Demand supported **HTML** file content (cornSpinach.html)

{% highlight html %}

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <body>
        <div class="e-content">
            <img src=" http://js.syncfusion.com/demos/web/images/accordion/corn-and-spinach-05.png" alt="corn-spinach"/>
            <div class="ingredients">
                Rate    : $70<br />
                Ingredients : cheese, sweet corn &amp; green capsicums. 
                    <br />
                Description: Small pizza bases are topped with spinach and paneer and fresh cream, a nice layer of mozzarella cheese. This is baked until the cheese is all hot and gooey.                   
            </div>
        </div>
    </body>
</html>

{% endhighlight %}

The Load On Demand supported html file content (chickenDelite.html)

{% highlight html %}

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <body>
        <div class="e-content">
            <img src="http://js.syncfusion.com/demos/web/images/accordion/chicken-delite.png" alt="chicken-delite"/>
            <div class="ingredients">
                Rate    : $100<br />
                Ingredients : cheese, chicken chunks, onions &amp; pineapple chunks.  
                <br />
                Description: This is a tasty, elegant chicken dish that is easy to prepare. 
            </div>
        </div>
    </body>
</html>

{% endhighlight %}

N> In Load On Demand, when the external files are referred from local the following error occurs.

XMLHttpRequest cannot load [http://js.syncfusion.com/UG/Web/Tab-Content/cornSpainach.html?_=1399883825133](http://js.syncfusion.com/UG/Web/Tab-Content/cornSpainach.html?_=1399883825133). No 'Access-Control-Allow-Origin' header is present on the requested resource. 

To avoid these errors, the external files are hosted in the server to run this application.

The following code example is used to position the image and content in Load On Demand.

{% highlight css %}

<style type="text/css" class="cssStyles">
   /*reuse the previous rating control style section code*/                
   .ingredients {
        height: 180px;
        margin-top: 8px;
    }
    img {           
        float: left;        
        margin: 10px 26px 5px 1px;
    }
</style>

{% endhighlight %}

The sub **Tab** control rendering script is represented in the following code example.

{% highlight js %}

    <script>
        angular.module('tabApp', ['ejangular'])
         .controller('TabCtrl', function ($scope) {
         });
    </script>

{% endhighlight %}

At the time of Ajax call, the content fetched from external file referenced location is illustrated in the following screenshot.

![](/js/Tab/Getting-Started_images/Getting-Started_img5.png) 

The following screenshot illustrates the First **Tab** with the sub **Tab** control using Load on Demand.

![](/js/Tab/Getting-Started_images/Getting-Started_img6.png) 

## Orientation Change

In this application, the sub **Tab** orientation needs to be vertical. By default, **Tab** control renders in horizontal orientation. Change the orientation to vertical using the “**headerPosition**” property. The **Tab** header orientation is set as “**left**”.

The following code example is used to render the sub **Tab** element in the vertical orientation.

{% highlight js %}

 <div id="dishType" ej-tab style="width: 550px ">
        <ul>
            <li><a href="#pizza">Pizza Menu</a></li>
            <li><a href="#sandwich">Sandwich Menu</a></li>
            <li><a href="#pasta">Pasta Menu</a></li>
        </ul>
        <div id="pizza" style="background-color: #F5F5F5">
            <p>Rating:</p>
            <!--Rating control declaration-->
            <div class="dishRating">
                <input id="pizzaRating" type="text" class="rating" ej-rating e-value="4.9" e-precision="Exact" />
            </div>
            <!--Food item description-->
            <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>
            <div id="pizzaType" ej-tab e-headerposition="left" e-height="221px">
                <ul>
                    <li><span class="cornSpinach"></span>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/cornSpainach.html">Corn & Spinach </a></li>
                    <li><span class="chickenDelite"></span>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/ChickenDelite.html">Chicken Delite </a></li>
                </ul>
            </div>
        </div>

    </div>

    <script>
        angular.module('tabApp', ['ejangular'])
         .controller('TabCtrl', function ($scope) {
         });
    </script>

{% endhighlight %}

The following screenshot illustrates the sub **Tab** with vertical orientation.

![](/js/Tab/Getting-Started_images/Getting-Started_img7.png) 

## Header Image Customization

In this application, you have to set the **Tab** header image for each Tab item to specify image in &lt;span&gt; tag element during the **Tab** header declaration time.	

The following code example is used for customizing the header image.

{% highlight css %}

<style type="text/css" class="cssStyles">
    .dish {
        display: inline-block;
        vertical-align: middle;
        margin: 0px -9px 0px 9px;            
    }
    .pizzaImg {
        background: url("http://js.syncfusion.com/UG/Web/Content/rsz_chicken-delite.png") no-repeat;
        height: 25px;
        width: 25px;
    }
    /*reuse the previous header orientation code*/                
</style>

{% endhighlight %}

The following code example is used to add the header image for the root **Tab** header element.

{% highlight html %}

<div id="dishType" style="width: 550px">
  <ul>
     <li><span class="dish pizzaImg"></span><a href="#pizza">Pizza Menu</a></li>  
     <!-- reuse the remaining tab header -->       
   </ul>
   <!-- reuse the previously defined first tab html content section-->
</div>

{% endhighlight %}

The following screenshot illustrates the **Tab** with the customized header image.

![](/js/Tab/Getting-Started_images/Getting-Started_img8.png) 

## Configuring Contents to remaining Tab items

The second and third **Tab** contents are declared in the same method as of the first **Tab** content declaration. These **Tabs** also consist of rating and sub **Tab** controls. The sub **Tab** control contents are loaded in Load On Demand support.

The following code example can be placed within the previous image customization **HTML** code section.

{% highlight html %}

 <!--reuse the first tab header defined in previous image customization -->
 <li><span class="dish sandwichImg"></span><a href="#sandwich">Sandwich Menu</a></li>
 <li><span class="dish pastaImg"></span><a href="#pasta">Pasta Menu</a></li>

{% endhighlight %}

Add the second **Tab** contents in &lt;div&gt; element during initialization.

{% highlight html %}

        <div id="sandwich" style="background-color: #F5F5F5">
            <p>Rating:</p>
            <!--Rating control declaration-->
            <div class="dishRating">
                <input id="sandwichRating" type="text" ej-rating class="rating" />
            </div>
            <!--dish description-->
            <p>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>
            <!--sub Tab control, the contents loaded with load on demand-->
            <div id="sandwichType" ej-tab>
                <ul>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/gardenVeggie.html">Garden Veggie </a></li>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/chickenTikka.html">Chicken Tikka </a></li>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/paneerTikka.html">Paneer Tikka </a></li>
                </ul>
            </div>
        </div>

{% endhighlight %}

Add third **Tab** contents in &lt;div&gt; element during initialization.

{% highlight html %}

        <div id="pasta" style="background-color: #F5F5F5">
            <p>Rating:</p>
            <!--Rating control declaration-->
            <div class="dishRating">
                <input id="pastaRating" type="text" ej-rating class="rating" />
            </div>
            <!--dish description-->
            <p>Pasta cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>
            <!--sub Tab control, the contents loaded with load on demand-->
            <div id="pastaType" ej-tab>
                <ul>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/khemmaPasta.html">Kheema Pasta </a></li>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/tunaPasta.html">Tuna Pasta</a></li>
                    <li>
                        <a href="http://js.syncfusion.com/UG/Web/Tab-Content/channaPasta.html">Channa Pasta
                        </a></li>
                </ul>
            </div>
        </div>

{% endhighlight %}

Apply the following styles to the **Tab**.

{% highlight css %}

<style type="text/css" class="cssStyles">
    /*to reuse the previous style section code and following css*/        
   .sandwichImg, .pastaImg {
        height: 25px;
        width: 25px;
    }
    .sandwichImg {
        background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-fresh.png") no-repeat;                       
    }
    .pastaImg {
        background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-veggie.png") no-repeat;                 
    }  
</style>

{% endhighlight %}

After the content declaration of all the **Tab** control, render the final output using the following code example.

{% highlight js %}


    <script>
        angular.module('tabApp', ['ejangular'])
         .controller('TabCtrl', function ($scope) {
         });
    </script>

{% endhighlight %}

The following screenshot illustrates you the second **Tab** contents in **Tab** and the final hotel menu with rating, description and ingredients of the item in the Tab interface.

![](/js/Tab/Getting-Started_images/Getting-Started_img9.png) 
