---
title: "toLocaleTimeString 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString 方法"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toLocaleTimeString 方法 (Date) (JavaScript)
返回作为适用于宿主环境的当前区域设置或指定区域设置的字符串值的时间。  
  
## 语法  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### 参数  
 `dateObj`  
 必需。  一个 `Date` 对象。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域设置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。  包含指定比较选项的一个或多个属性的对象。  
  
## 备注  
 从 Internet Explorer 11 开始，`toLocaleTimeString` 在内部使用 `Intl.DateTimeFormat` 来设置时间的格式，这可增加对 `locales` 和 `options` 参数的支持。  有关这些参数的详细信息，请参阅 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  不是所有文档模式和浏览器版本中都支持 `locales` 和 `options` 参数。  有关详细信息，请参阅“要求”一节。  
  
 当你在 Internet Explorer 10 标准文档模式、较早的文档模式和 Quirks 模式中使用 `toLocaleTimeString` 时：  
  
-   它返回一个包含当前所在时区中的某个时间的字符串值。  
  
-   返回的时间是宿主环境的当前区域设置的默认格式。  
  
 如果省略 `locales` 参数，此方法的返回值不能依赖于编写脚本，因为它会因计算机的不同而有所变化。  在此方案中，仅使用该方法设置显示文本的格式，即永远不会作为计算的一部分。  
  
## 示例  
 下面的示例演示如何将 `toLocaleTimeString` 方法用于指定的区域设置和比较选项。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toTimeString 方法 \(Date\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString 方法 \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)