---
title: "内部对象 (JavaScript) | Microsoft Docs"
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
  - "内置对象 [JavaScript]"
  - "内部对象 [JavaScript]"
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 内部对象 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供了内部（或“内置”）对象。  它们是 `Array`、`Boolean`、`Date`、`Error`、`Function`、**Global**、**JSON**、**Math**、**Number**、`Object`、`RegExp` 和 `String` 对象。  内部对象具有[语言参考](../javascript/reference/javascript-reference.md)中详细描述的关联方法、函数、属性和常量。  
  
## Array 对象  
 数组的下标可被视为对象的属性，且通过其数字索引进行引用。  请注意，添加到数组的命名属性不能按数字进行索引；它们独立于数组元素。  
  
 若要创建新数组，请使用 **new** 运算符和 **Array \(\)** [构造函数](../javascript/reference/constructor-property-object-javascript.md)，如以下示例所示。  
  
```javascript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 使用 `Array` 关键字创建数组时，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 会包括记录项的数目的 **length** 属性。  如果未指定数字，则长度设置为 0 且数组没有任何项。  如果指定一个数字，则长度设置为此数字。  如果指定多个参数，则参数将用作数组中的项。  此外，将参数数目分配给 length 属性，如以下示例（等效于先前示例）中所示。  
  
```javascript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 将元素添加到使用 `Array` 关键字创建的数组时，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 将自动更改 **length** 的值。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的数组索引始终从 0（而不是 1）开始，因此 length 属性值始终比数组中的最大索引大 1。  
  
## String 对象  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，可以将字符串（和数字）当做对象对待。  [string 对象](../javascript/reference/string-object-javascript.md)具有一些可与字符串一起使用的内置方法。  其中之一即是 [substring 方法](../javascript/reference/substring-method-string-javascript.md)，它返回字符串中的一部分。  它将两个数字视为其参数。  
  
```javascript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 `String` 对象的另一个属性是 **length** 属性。  此属性包含字符串中的字符数（空字符串则为 0）。  这是一个数值且可直接用于计算。  
  
```javascript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## Math 对象  
 **Math** 对象具有大量预定义的常量和函数。  常量是指特定数字。  其中一个特定数字是 pi 值（约为 3.14159...）。  这是 **Math.PI** 常量，如以下示例所示。  
  
```javascript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 **Math** 对象的其中一个内置函数是求幂方法（即 `Math.pow`），它将数字与指定幂数相乘。  下面的示例使用 pi 和求幂来计算球的体积。  
  
```javascript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## Date 对象  
 `Date` 对象可用于表示任意日期和时间，以获取当前系统日期，并计算两个日期的时间差。  它具有多个属性和方法，且都是预定义的。  一般情况下，`Date` 对象提供星期几；月、日和年；以及以小时、分钟和秒为单位的时间。  此信息取决于自 1970 年 1 月 1 日 00:00:00.000 GMT 以来的毫秒数，这是格林威治标准时间（首选的词条是 UTC 或“协调世界时”，它指由世界时间标准颁发的信号）。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 可以处理大致介于公元前 250,000 年  到公元 255,000 年间的日期  
  
 若要创建新的 `Date` 对象，请使用 **new** 运算符，如以下示例所示。  
  
```javascript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## Number 对象  
 除了 **Math** 对象中提供的特殊数值常量（例如 `PI`），还可以在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中通过 **Number** 对象使用多个其他常量。  
  
|返回的常量|描述|  
|-----------|--------|  
|Number.MAX\_VALUE|最大可能值，约为 1.79E\+308；正数和负数皆可。  （系统不同，值略有不同。）|  
|Number.MIN\_VALUE|最小可能值，约为 5.00E\-324；正数和负数皆可。  （系统不同，值略有不同。）|  
|Number.NaN|特殊的非数字值，“不是数字。”|  
|Number.POSITIVE\_INFINITY|大于最大正数 \(Number.MAX\_VALUE\) 的任何正值均自动转换为此值；该值表示为无穷大。|  
|Number.NEGATIVE\_INFINITY|小于最大负数 \(\-Number.MAX\_VALUE\) 的任何负值均自动转换为此值；该值表示为负无穷大。|  
  
 **Number.NaN** 是一个定义为“不是数字”的特殊常量。 尝试分析无法被分析为数字的字符串的操作将返回 **Number.NaN**。  `NaN` 与任意数字及自身比较时都不相等。  若要测试 `NaN` 结果，请不要与 **Number.NaN** 比较；请改用 **isNaN\(\)** 函数。  
  
## JSON 对象  
 JSON 是基于 JavaScript 语言的对象文本表示法子集的一种轻型数据交换格式。  
  
 JSON 对象提供了两个函数，用于转换为 JSON 文本格式和从 JSON 文本格式转换。  [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) 函数将对象和数组序列化为 JSON 文本。  [JSON.parse](../javascript/reference/json-parse-function-javascript.md) 函数反序列化 JSON 文本以生成内存中对象。  有关详细信息，请参阅 [JavaScript 和 .NET 中 JavaScript 对象表示法 \(JSON\) 的简介](http://go.microsoft.com/fwlink/?LinkId=124098)。  
  
## 请参阅  
 [JavaScript 对象](../javascript/reference/javascript-objects.md)