---
layout: post
title: Exporting-the-Digital-Gauge
description: exporting the digital gauge
platform: AngularJS
control: Digital Gauge
documentation: ug
---

# Exporting the Digital Gauge

**Digital Gauge** has an exporting feature where **Gauge** control is converted into image format and then exported to client-side. The method API **exportImage** exports the **Digital Gauge**. It has two arguments such as **file****name** and **file format**. For exporting, you can refer the following code example.

{% highlight html %}

<div id="DigitalGauge1" ej-digitalgauge e-value="SYNCFUSION"></div>
<button id="buttonSubmit">Export</button>
<div id=" fileName ">FileName </div>
<input type="text" id="fileName"/>
<div id=" fileFormat ">FileFormat </div>
<select id="fileFormat">
<option value="JPEG">JPEG</option>
<option value="PNG">PNG</option>
</select>

{% endhighlight %}

{% highlight javascript %}

     $(function () {
        $("#buttonSubmit").ejButton({ width: "50px", text: "Export", click: "buttonClickEvent", });
        $("#fileFormat").ejDropDownList({ selectedItemIndex: 0, width: "115px" });
        
    });
    $("# DigitalGauge1").ejDigitalGauge("exportImage", "Digital", "JPEG");
    function buttonClickEvent() {
        var FileName = $("#fileName").val();
        var FileFormat = $("#fileFormat").ejDropDownList("option", "value");
        var flag = $("#DigitalGauge1").ejDigitalGauge("exportImage", FileName, FileFormat);
        if (!flag)
            alert("Sorry for the inconvenience. Export is currently not supported in Internet Explorer 9 and below version");
    }


{% endhighlight %}

Execute the above code examples to render the **Digital****Gauge** as follows.

![](/js/DigitalGauge/Exporting-the-Digital-Gauge_images/Exporting-the-Digital-Gauge_img1.png)

