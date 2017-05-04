---
title: "日期和时间字符串 (JavaScript) | Microsoft Docs"
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
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: 47
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 47
---
# 日期和时间字符串 (JavaScript)
可以使用多种方法来指定 JavaScript 日期和时间字符串并设置其格式。  
  
## 使用 Intl.DateTimeFormat 设置日期格式  
 Internet Explorer 11 引入了对 [Intl.DateTimeFormat 对象](../javascript/reference/intl-datetimeformat-object-javascript.md) 对象的支持，此对象是 [ECMAScript 国际化 API 规范](http://www.ecma-international.org/ecma-402/1.0/)的一部分。  若要设置日期格式，可直接使用此对象，也可使用 [toLocaleDateString 方法 \(Date\)](../javascript/reference/tolocaledatestring-method-date-javascript.md) 和 [toLocaleTimeString 方法 \(Date\)](../javascript/reference/tolocaletimestring-method-date-javascript.md) 的更新实现。  [Date 对象](../javascript/reference/date-object-javascript.md) 的这些方法在内部使用 `Intl.DateTimeFormat` 以支持用于区域设置和其他格式设置选项的新的可选参数。  
  
 以下示例演示如何使用 `toLocaleDateString` 和 `toLocaleTimeString` 设置日期和时间格式。  传递给这些方法的第一个参数是区域设置值，例如“en\-us”。  第二个参数（如果存在）指定格式设置选项（如周日期的长格式）。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 有关格式设置选项的完整列表，请参见 [Intl.DateTimeFormat 对象](../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
## 设置日期格式  
 在 Internet Explorer 11 之前，JavaScript 没有设置日期和时间格式的特定方法。  若要对先前的浏览器版本提供你自己的日期格式，请使用 [getDay 方法 \(Date\)](../javascript/reference/getday-method-date-javascript.md)、[getDate 方法 \(Date\)](../javascript/reference/getdate-method-date-javascript.md)、[getMonth 方法 \(Date\)](../javascript/reference/getmonth-method-date-javascript.md) 和 [getFullYear 方法 \(Date\)](../javascript/reference/getfullyear-method-date-javascript.md) 方法。  （[getYear 方法 \(Date\)](../javascript/reference/getyear-method-date-javascript.md) 已过时且不应使用。）  
  
```javascript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 你可以通过使用 [getHours 方法 \(Date\)](../javascript/reference/gethours-method-date-javascript.md)、[getMinutes 方法 \(Date\)](../javascript/reference/getminutes-method-date-javascript.md)、[getSeconds 方法 \(Date\)](../javascript/reference/getseconds-method-date-javascript.md) 和 [getMilliseconds 方法 \(Date\)](../javascript/reference/getmilliseconds-method-date-javascript.md) 方法提供自己的时间格式。  
  
```javascript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +  
":" + myDate.getMilliseconds());  
  
// Output:  
// 10:30:53:400  
```  
  
## 将字符串转换为日期  
 你可以使用 `Date(dateStr)` 或 `Date.parse(dateStr)` 指定构造 `Date` 对象的字符串。  JavaScript 使用以下规则来分析日期字符串：  
  
-   它首先尝试使用 [ISO 日期格式](#ISO) 来分析日期字符串。  
  
    > [!NOTE]
    >  JavaScript 使用 ISO 8601 扩展格式的简化版本。  
  
-   如果日期字符串未采用 ISO 格式，则 JavaScript 会尝试使用其他 [其他日期格式](#OtherDateFormats) 来分析日期。  
  
<a name="ISO"></a>   
## ISO 日期格式  
 ISO 格式是 ISO 8601 扩展格式的简化形式。  格式如下所示：  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  ISO 日期格式在 Internet Explorer 8 标准模式和 Quirks 模式中不受支持。  
  
 下表介绍了此格式的各个部分。  
  
|符号|描述|值|  
|--------|--------|-------|  
|`-`, `:`, `.`, `T`|字符串中的实际字符。  `T` 指定某个时间的开始。||  
|`YYYY`|年份。  可使用扩展的年份来代替 4 位数年份。  有关详细信息，请参阅本主题后面的 [扩展的年份](../javascript/date-and-time-strings-javascript.md#bkmk_extend)。||  
|`MM`|月份|01 到 12|  
|`DD`|一个月中的某一天|01 到 31|  
|`HH`|小时|00 到 24|  
|`mm`|分钟|00 到 59|  
|`ss`|秒。  如果指定了时间，则秒和毫秒是可选项。|00 到 59|  
|`sss`|毫秒|00 到 999|  
|`Z`|此位置的值可以是下列值之一。  如果省略此值，则使用 UTC 时间。<br /><br /> -   `Z` 指示 UTC 时间。<br />-   `+hh:mm` 指示输入时间是 UTC 时间后的指定偏移量。<br />-   `-hh:mm` 指示输入时间是 UTC 时间前的指定偏移量的绝对值。||  
  
 字符串只能包含以下格式的日期：`YYYY`、`YYYY-MM`、`YYYY-MM-DD`。  
  
 ISO 格式不支持时区名称。  可使用 `Z` 位置来指定相对于 UTC 时间的偏移量。  如果未在 `Z` 位置包括一个值，则使用 UTC 时间。  
  
 可使用 00:00 或前一天的 24:00 指定午夜。  以下两个字符串指定同一时间：2010\-05\-25T00:00 和 2010\-05\-24T24:00。  
  
 若要返回 ISO 格式的日期，可使用 [toISOString 方法 \(Date\)](../javascript/reference/toisostring-method-date-javascript.md)。  
  
<a name="bkmk_extend"></a>   
### 扩展的年份  
 扩展的年份具有 6 位数而不是 4 位数，并以加号或减号作为前缀。  例如，`+002010` 是一个扩展的年份，它等同于 `2010`。  可使用扩展的年份来表示在年份 0 之前或年份 9999 之后的年份。  
  
 如果使用 6 位数格式，则必须有加号或减号。  在使用 4 位数格式时，不能存在加号或减号。  因此，系统会接受 `0000` 和 `+000000`，而 `000000` 和 `-0001` 会导致错误。  扩展的年份 0 被视为正数，并以加号作为前缀。  
  
 [toISOString 方法 \(Date\)](../javascript/reference/toisostring-method-date-javascript.md) 始终对年份 0 之前和年份 9999 之后的年份使用扩展的年份格式。  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## 其他日期格式  
 如果日期字符串未采用 ISO 格式，则 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 将使用以下规则对其进行分析。  
  
 短日期  
  
-   该格式必须遵循月\/日\/年顺序，如“06\/08\/2010”。  
  
-   “\/”或“\-”可用作分隔符。  
  
 长日期  
  
-   年、月和日可按任何顺序排列。“  June 8 2010”和“2010 June 8”均有效。  
  
-   年份可具有 2 位或 4 位数。  如果年份只有 2 位数，则它必须至少为 70。  
  
-   月和日的名称必须至少具有两个字符。  两个字符所组成的非唯一名称将解析为最后一个匹配名称。  例如，“Ju”表示 7 月而不是 6 月。  
  
-   如果一周中的某天与所提供日期的其余部分不一致，则忽略该天。  例如，“Tuesday November 9 1996”解析为“Friday November 9 1996”，因为 Friday 是与该日期对应的正确周日期。  
  
 时间  
  
-   小时、分钟和秒用冒号分隔开。  但可省略某些部分。  以下各项均有效：“10:”、“10:11”和“10:11:12”。  
  
-   如果指定 PM 且指定的小时至少为 13，则返回 NaN。  例如，“23:15 PM”返回 NaN。  
  
 常规  
  
-   包含无效日期的字符串将返回 NaN。  例如，包含两个年份或两个月份的字符串将返回 NaN。  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支持所有标准时区、协调通用时间 \(UTC\) 和格林尼治标准时间 \(GMT\)。  （ISO 格式不支持时区。）  
  
-   括号中的文本被视为注释。  括号可以嵌套。  
  
-   逗号和空格被视为分隔符。  允许使用多个分隔符。  
  
## 示例  
 下面的代码显示分析不同的日期和时间字符串所获得的结果。  
  
```  
document.writeln((new Date("2010")).toUTCString());  
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 在指定了本地时间的情况下，结果将随时区的不同而不同。  
  
> [!IMPORTANT]
>  ISO 日期格式在 Internet Explorer 8 标准模式和 Quirks 模式中不受支持。  
  
## 请参阅  
 [Date 对象](../javascript/reference/date-object-javascript.md)   
 [Date.parse 函数](../javascript/reference/date-parse-function-javascript.md)