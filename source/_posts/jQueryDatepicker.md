---
title: jQuery Datepicker
date: 2022-08-16 11:34
categories:
  - jQuery
tags:
  - jQuery
  - Datepicker
---
使用Datepicker 套件來顯示日期選擇器

<!--more-->
寫網頁有時候就會用到日期，
為了不要每次寫的時候都要花費一些時間尋找，
紀錄起來方便之後使用，靠小腦袋基本上靠不住>///<
### html
```
<p>日期: <input type="text" id="datepicker"></p> 
```
### jQuery(單一日期)
```
<!--jQuery datepicker 開始-->
  <link rel="stylesheet" href="https://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
  <link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
  <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  <script src="http://tony1966.xyz/test/jquery/jquery.ui.datepicker-zh-TW.js"></script>
  <script>
    $(function () {
      $("#datepicker").datepicker({
        dateFormat: "yy-mm-dd",
        defaultDate: "+0w",
        changeMonth: true,
        numberOfMonths: 1,
        changeYear: true,
        //showOn: "button",
        //minDate: "-0d" //不可選取過去日期
      });
    });
  </script>
```
### jQuery(日期範圍)
```
<!--jQuery datepicker 開始-->
<link rel="stylesheet" href="https://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
<link rel="stylesheet" href="http://jqueryui.com/resources/demos/style.css">
<script src="https://code.jquery.com/jquery-1.12.4.js"></script>
<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
<script src="http://tony1966.xyz/test/jquery/jquery.ui.datepicker-zh-TW.js"></script>
<script>
    $(function () {
    var dateFormat = "yymmdd",
    from = $("#ContentPlaceHolder1_datepicker1").datepicker({
    dateFormat: "yymmdd",
    defaultDate: "+0w",
    changeMonth: true,
    numberOfMonths: 1,
    changeYear: true,
    showOn: "button",
    buttonImage: "/images/date.png",
    buttonImageOnly: true,
    buttonText: "Select date"
})
    .on("change", function () {
        to.datepicker("option", "minDate", getDate(this));
    }),
    to = $("#ContentPlaceHolder1_datepicker2").datepicker({
    dateFormat: "yymmdd",
    defaultDate: "+0w",
    changeMonth: true,
    numberOfMonths: 1,
    changeYear: true,
    showOn: "button",
    buttonImage: "/images/date.png",
    buttonImageOnly: true,
    buttonText: "Select date"
})
    .on("change", function () {
        from.datepicker("option", "maxDate", getDate(this));
    });

    function getDate(element) {
    var date;
    try {
        date = $.datepicker.parseDate(dateFormat, element.value);
    } catch (error) {
        date = null;
    }
    return date;
        }
    });
</script>
<!--jQuery datepicker 結束-->
```
### 參考資料
[jQuery Datepicker](https://jqueryui.com/datepicker/)