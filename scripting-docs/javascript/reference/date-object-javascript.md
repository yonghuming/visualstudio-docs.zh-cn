---
title: "Date 对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Date 对象 (JavaScript)
支持基本的存储以及日期和时间的检索。  
  
## <a name="syntax"></a>语法  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 `Date` 对象分配到的变量名称。  
  
 `dateVal`  
 必需。 如果是数值，`dateVal`表示协调世界时在指定的日期和 1970 年 1 月 1 日午夜之间的毫秒数。 如果是字符串，`dateVal`的分析将遵照中的规则[日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)。 `dateVal`参数也可以是 VT_DATE 值返回从某些 ActiveX 对象。  
  
 `year`  
 必需。 完整年，例如，1976年 （和不 76）。  
  
 `month`  
 必需。 月份，介于 0 和 11 （一月到十二月） 之间的整数。  
  
 `date`  
 必需。 日期介于 1 和 31 之间的整数。  
  
 `hours`  
 可选。 如果必须提供`minutes`提供。 从 0 到 23 （午夜到晚上 11 点） 的整数，指定的小时。  
  
 分钟  
 可选。 如果必须提供`seconds`提供。 一个从 0 到 59 之间的整数，指定的分钟数。  
  
 `seconds`  
 可选。 如果必须提供`milliseconds`提供。 一个从 0 到 59 之间的整数，指定的秒数。  
  
 `ms`  
 可选。 一个从 0 到 999 之间的整数，指定毫秒数。  
  
## <a name="remarks"></a>备注  
 A`Date`对象包含到时间内的时间以毫秒为单位表示某个特定时刻的数字。 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果你指定 150 秒[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]重数定义为两个分 30 秒。  
  
 如果数字为`NaN`，该对象不表示特定即时。 如果你没有将参数传递给`Date`对象，它将初始化为当前时间 (UTC)。 你可以使用它之前，必须对对象给定值。  
  
 可在中表示的日期范围内`Date`对象是自 1970 年 1 月 1 日的任何一侧大约 285616 年。  
  
 请参阅[计算日期和时间 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)详细了解如何使用`Date`对象和相关的方法。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Date` 对象的用法。  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>要求  
 `Date object`中已引入 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]。 更高版本中已引入以下列表中的某些成员。 有关详细信息，请参阅[版本信息](../../javascript/reference/javascript-version-information.md)或各个成员的文档。  
  
## <a name="properties"></a>属性  
 下表列出了 `Date Object` 的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[constructor 属性](../../javascript/reference/constructor-property-date.md)|指定用于创建对象的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-date.md)|为对象的类返回原型的引用。|  
  
## <a name="functions"></a>函数  
 下表列出了 `Date Object` 的函数。  
  
|函数|描述|  
|---------------|-----------------|  
|[Date.now 函数](../../javascript/reference/date-now-function-javascript.md)|返回自 1970 年 1 月 1 日之间的毫秒数以及当前日期和时间。|  
|[Date.parse 函数](../../javascript/reference/date-parse-function-javascript.md)|分析包含日期的字符串并返回该日期和 1970 年 1 月 1 日午夜之间的毫秒数。|  
|[Date.UTC 函数](../../javascript/reference/date-utc-function-javascript.md)|返回自 1970 年 1 月 1 日午夜之间的毫秒数协调世界时 (UTC) （或格林威治标准时间） 和所提供的日期。|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>方法  
 下表列出了 `Date Object` 的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|返回使用本地时间的月日期值。|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|返回使用本地时间的星期日期值。|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|返回使用本地时间的年份值。|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|返回使用本地时间的小时值。|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|返回毫秒值使用本地时间。|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|返回使用本地时间的分钟值。|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|返回使用本地时间的月份值。|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|使用本地时间返回秒值。|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|返回的时间值以`Date`对象作为自 1970 年 1 月 1 日午夜以来的毫秒数。|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|返回以分钟为单位主机计算机上的时间和协调世界时 (UTC) 之间的差异。|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|返回使用 UTC 的月日期值。|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|返回使用 UTC 的星期日期值。|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|返回使用 UTC 的年份值。|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|返回使用 UTC 的小时值。|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|返回毫秒值使用 UTC。|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|返回使用 UTC 的分钟值。|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|返回使用 UTC 的月份值。|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|返回秒值使用 UTC。|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|返回中的 VT_DATE 值`Date`对象。|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|返回年份值。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否具有指定名称的属性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型链中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|设置使用本地时间的月份的数字天。|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)|设置使用本地时间的年份值。|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|设置使用本地时间的小时值。|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|设置使用本地时间的毫秒值。|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|设置使用本地时间的分钟值。|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|设置使用本地时间的月份值。|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|设置秒值使用本地时间。|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|设置日期和时间值以`Date`对象。|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|设置使用 UTC 的月份的数字天。|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|设置使用 UTC 的年份值。|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|设置使用 UTC 的小时值。|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|设置使用 UTC 毫秒值。|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|设置使用 UTC 的分钟值。|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|设置使用 UTC 的月份值。|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|设置秒值使用 UTC。|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|设置使用本地时间的年份值。|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|返回一个字符串值作为日期。|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|返回的日期转换为字符串使用格林威治标准时间 (GMT)。|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|返回采用 ISO 格式的日期为一个字符串值。|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|用于转换的 JSON 序列化之前的对象类型的数据。|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|返回一个字符串值日期适合于宿主环境的当前区域设置。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-date.md)|返回转换为使用当前区域设置字符串的对象。|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|返回作为一个字符串值的时间适合于宿主环境的当前区域设置。|  
|[toString 方法](../../javascript/reference/tostring-method-date.md)|返回对象的字符串表示形式。|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|返回作为一个字符串值的时间。|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|返回转换为字符串使用 UTC 日期。|  
|[valueOf 方法](../../javascript/reference/valueof-method-date.md)|返回指定对象的基元值。|  
  
## <a name="see-also"></a>另请参阅  
 [计算日期和时间 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)