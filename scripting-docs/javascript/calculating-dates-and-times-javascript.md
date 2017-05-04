---
title: "计算日期和时间 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期和时间计算 [JavaScript]"
  - "JavaScript，日期和时间"
  - "日期比较 [JavaScript]"
  - "日期和时间计算 [JavaScript]"
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# 计算日期和时间 (JavaScript)
可使用 [Date 对象](../javascript/reference/date-object-javascript.md)来执行常见的日历和时钟任务，如比较日期和计算经过的时间。  
  
## 将日期设置为当前日期  
 在不指定日期的情况下创建 [Date 对象](../javascript/reference/date-object-javascript.md)的实例时，将返回一个值，该值表示当前日期和时间，包括年、月、日、小时、分钟、秒和毫秒。  然后，你可以读取或修改此日期和时间。  
  
 以下示例演示如何在不使用任何参数的情况下实例化日期，并采用 *mm\-dd\-yy* 格式显示该日期。  
  
```javascript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## 设置特定日期  
 可以通过将日期字符串传递给构造函数来设置特定日期。  
  
```javascript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  日期字符串中显示的时区对应于本地计算机上设置的时区。  
>   
>  对于用作参数的字符串格式，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 很灵活。  例如，可以输入“8\-24\-2009”、“August 24, 2009”或“24 Aug 2009”。  
  
 你还可以指定某个时间。  以下示例演示按 ISO 格式指定日期和时间的一种方式。  “Z”指示 UTC 时间。  
  
```javascript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 有关日期格式（如 ISO）的更多信息，请参见[日期和时间字符串](../javascript/date-and-time-strings-javascript.md)。  
  
 以下示例演示指定时间的其他方式。  
  
```javascript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## 增加和减少天数、月数和年数  
 可使用 `Date` 对象的 getX 和 setX 方法来设置特定日期和时间。  
  
 以下示例演示如何将日期设置为前一天的日期。  请注意，如有必要，还可以更改月份和年份值。  
  
```javascript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 以下示例通过从下个月第一天的日期中减去一天来将日期设置为该月的最后一天。  
  
> [!TIP]
>  年中月份的编号介于 0（1 月）和 11（12 月）之间。  周日期的编号介于 0（星期日）和 6（星期六）之间。  
  
```javascript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## 处理周日期  
 [getDay 方法](../javascript/reference/getday-method-date-javascript.md)获取以介于 0（星期日）和 6（星期六）之间的数字表示的周日期。（这与 [getDate 方法](../javascript/reference/getdate-method-date-javascript.md)不同，后者将获取以介于 1 和 31 之间的数字表示的月日期）。  
  
 以下示例设置感恩节的日期，该日期在美国为十一月的第四个星期四。  该脚本先找到当前年份的 11 月 1 日，再找到第一个星期四，然后增加三周。  
  
```javascript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## 计算经过的时间  
 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)返回自 1970 年 1 月 1 日午夜起经过的毫秒数。  对于该日期之前的任何日期，将返回一个负数。  
  
 可使用 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)来设置开始时间和结束时间以计算经过的时间。  它可用于测量较小单位（如秒数）和较大单位（如天数）。  
  
 以下示例计算经过的时间（以秒为单位）。  [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)获取从零日期后经过的毫秒数。  
  
```javascript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 若要使用更易于管理的单位，可以将 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)提供的毫秒数除以某个适当的数字。  例如，若要将毫秒数转换为天数，可以将毫秒数除以 86,400,000（1000 毫秒 x 60 秒 x 60 分 x 24 小时）。  
  
 以下示例演示自指定年份的第一天起经过的时间。  它使用除法运算来计算经过的时间（以天、小时、分钟和秒为单位）。  此示例不考虑夏时制时间。  
  
```javascript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### 确定用户的年龄  
 以下示例通过用户的生日来计算用户在各个年份的年龄。  此示例用当前年份减去用户的出生年份，如果用户在当前年份中的生日目前还没有到，则再减去 1。  
  
```javascript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## 比较日期  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中比较日期时，应记住仅当 `==` 运算符两边的日期引用同一个对象时，该运算符才返回 `true`。  因此，如果将两个单独的 `Date` 对象设置为同一个日期，则 `date1 == date2` 返回 `false`。  此外，仅包含日期而非时间的 `Date` 对象集将初始化为该日期的午夜。  因此，如果将一个不带指定时间的 `Date` 集与 `Date.now` 进行比较，应注意第一个 `Date` 将设置为午夜，而 `Date.now` 不会如此。  
  
 以下示例检查当前日期是在指定日期当天、之前还是之后。  为了在 `todayAtMidn` 中设置当前日期，该脚本会为当前年份、月份和天创建 `Date` 对象。  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 通过修改前面的示例，可检查提供的日期是否在特定范围内。  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## 请参阅  
 [Date 对象](../javascript/reference/date-object-javascript.md)