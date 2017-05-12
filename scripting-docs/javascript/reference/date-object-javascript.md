---
title: "Date 对象 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 对象"
  - "日期, 确定"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Date 对象 (JavaScript)
启用日期和时间的基本存储和检索。  
  
## 语法  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## 参数  
 `dateObj`  
 必需。  `Date` 对象分配到的变量名称。  
  
 `dateVal`  
 必需。  如果是数值，`dateVal` 表示指定日期与 1970 年 1 月 1 日午夜之间相差的协调世界时的毫秒数。  如果是字符串，则根据 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md) 中的规则分析 `dateVal`。  `dateVal` 参数也可以是从一些 ActiveX 对象返回的 VT\_DATE 值。  
  
 `year`  
 必需。  年份全称，如 1976（而不是 76）。  
  
 `month`  
 必需。  月份，用从 0 到 11 的整数表示（1 月至 12 月）。  
  
 `date`  
 必需。  日期，用从 1 到 31 的整数表示。  
  
 `hours`  
 可选。  如果提供了 `minutes` 参数，那么必须提供此参数。  一个指定小时的，从 0 到 23 的整数（午夜到 11pm）。  
  
 分钟  
 可选。  如果提供了 `seconds` 参数，那么必须提供此参数。  一个指定分钟的，从 0 到 59 的整数。  
  
 `seconds`  
 可选。  如果提供了 `milliseconds` 参数，那么必须提供此参数。  一个指定秒的，从 0 到 59 的整数。  
  
 `ms`  
 可选。  一个指定毫秒的，从 0 到 999 的整数。  
  
## 备注  
 `Date` 对象包含表示具体时间（可以精确到毫秒）的数字。  如果参数值大于其取值范围或者为负，则会相应地修改存储的其他值。  例如，如果指定 150 秒，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将该数字重新定义为 2 分 30 秒。  
  
 如果数字是 `NaN`，则对象不表示特定的时间时刻。  如果没有将任何参数传递到 `Date` 对象，该函数将初始化为当前时间 \(UTC\)。  必须先为对象赋值，然后才能使用它。  
  
 可在 `Date` 对象中表示的日期范围大约为 1970 年 1 月 1 日左右的 285,616 年。  
  
 有关如何使用 `Date` 对象和相关方法的更多信息，请参见[计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 示例  
 下面的示例阐释了 `Date` 对象的用法。  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## 要求  
 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] 中已引入 `Date object`。  更高版本中已引入以下列表中的某些成员。  有关更多信息，请参见 [版本信息](../../javascript/reference/javascript-version-information.md)或与单个成员对应的文档。  
  
## 属性  
 下表列出了 `Date Object` 的属性。  
  
|Property|描述|  
|--------------|--------|  
|[constructor 属性](../../javascript/reference/constructor-property-date.md)|指定创建一个对象的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-date.md)|为对象的类返回原型的引用。|  
  
## 函数  
 下表列出了 `Date Object` 的函数。  
  
|函数|描述|  
|--------|--------|  
|[Date.now 函数](../../javascript/reference/date-now-function-javascript.md)|返回 1970 年 1 月 1日与当前日期和时间之间的毫秒数。|  
|[Date.parse 函数](../../javascript/reference/date-parse-function-javascript.md)|分析一个包含日期的字符串，并返回该日期与 1970 年 1 月 1 日午夜之间相差的毫秒数。|  
|[Date.UTC 函数](../../javascript/reference/date-utc-function-javascript.md)|返回协调通用时间 \(UTC\)（或 GMT）1970 年 1 月 1 日午夜与所提供的日期之间相差的毫秒数。|  
  
<a name="js56jsobjdatemeth"></a>   
## 方法  
 下表列出了 `Date Object` 的方法。  
  
|方法|描述|  
|--------|--------|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|使用当地时间返回一个月某天的值。|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|使用当地时间返回一个星期某天的值。|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|使用当地时间返回年份值。|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|使用当地时间返回小时值。|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|使用当地时间返回毫秒值。|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|使用当地时间返回分钟值。|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|使用当地时间返回月份值。|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|使用当地时间返回秒值。|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|将 `Date` 对象中的时间值返回为自 1970 年 1 月 1 日午夜起经过的毫秒数。|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|返回主机的时间与协调通用时间 \(UTC\) 之间的分钟差值。|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|使用 UTC 返回一个月某天的值。|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|使用 UTC 返回一个星期某天的值。|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|使用 UTC 返回年份值。|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|使用 UTC 返回小时值。|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|使用 UTC 返回毫秒值。|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|使用 UTC 返回分钟值。|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|使用 UTC 返回月份值。|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|使用 UTC 返回秒值。|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|将 `Date` 对象中的 VT\_DATE 值返回。|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|返回年份值。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示一个对象是否具有指定名称的属性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示对象是否存在于另一个对象的原型链中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分以及该属性是否是可枚举的。|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|使用当地时间设置一个月中某一日的数值。|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)|使用当地时间设置年份值。|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|使用当地时间设置小时值。|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|使用当地时间设置毫秒值。|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|使用当地时间设置分钟值。|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|使用当地时间设置月份值。|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|使用当地时间设置秒值。|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|设置 `Date` 对象中的日期和时间值。|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|使用 UTC 设置一个月中某一日的数值。|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|使用 UTC 设置年份值。|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|使用 UTC 设置小时值。|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|使用 UTC 设置毫秒值。|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|使用 UTC 设置分钟值。|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|使用 UTC 设置月份值。|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|使用 UTC 设置秒值。|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|使用当地时间设置年份值。|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|以字符串值的形式返回一个日期。|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|返回使用格林尼治标准时间 \(GMT\) 转换为字符串的日期。|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|以字符串值的形式返回采用 ISO 格式的日期。|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|用于在 JSON 序列化之前转换目标类型的数据。|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|将一个日期以字符串值的形式返回，该字符串应适合于宿主环境的当前区域设置。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-date.md)|返回使用当前区域设置转换为字符串的对象。|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|以字符串值的形式返回一个时间，此字符串值应与宿主环境的当前区域设置相适应。|  
|[toString 方法](../../javascript/reference/tostring-method-date.md)|返回表示对象的字符串。|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|以字符串值形式返回时间。|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|返回使用 UTC 转换为字符串的日期。|  
|[valueOf 方法](../../javascript/reference/valueof-method-date.md)|返回指定对象的原始值。|  
  
## 请参阅  
 [计算日期和时间 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)