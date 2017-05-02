---
title: "toLocaleString (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
使用当前区域设置或指定的区域设置将日期转换为字符串。  
  
## 语法  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### 参数  
 `dateObj`  
 必需。  要转换的 `Date` 对象。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。  包含一个或多个指定比较选项的特性的对象。  
  
## 备注  
 从 Internet Explorer 11 开始，`toLocaleString` 在内部使用 `Intl.DateTimeFormat` 进行比较，添加对 `locales` 和 `options` 参数的支持。  有关这些参数的详细信息，请参见 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  `locales` 和 `options` 参数在所有的文档模型和浏览器版本中均不支持。  有关详细信息，请参见“要求”部分。  
  
 在 Internet Explorer 10 标准文档模式、早期文档模式和突发模式下使用 `toLocaleString` 时：  
  
-   其返回一个 `String` 对象，此对象包含以当前区域设置的长默认格式编写的日期。  
  
-   对于公元 1601 和 1999 之间的日期，其格式将根据用户在“控制面板”中选择的“区域设置”确定。  
  
> [!NOTE]
>  如果您忽略 `locales` 参数，请使用 `toLocaleString` 仅向用户显示结果；请勿用其在脚本中计算值，因为返回的结果是计算机特定的。  
  
## 示例  
 下面的示例演示如何使用 `toLocaleString` 方法。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 示例  
 下面的示例显示如何使用带指定区域设置和比较选项的 `toLocaleString` 方法。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toLocaleDateString 方法 \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)