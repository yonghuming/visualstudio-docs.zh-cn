---
title: "toLocaleDateString 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString 方法"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLocaleDateString 方法 (Date) (JavaScript)
将一个日期以字符串值的形式返回，该字符串应适合于宿主环境的当前区域设置或指定的区域设置。  
  
## 语法  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### 参数  
 `dateObj`  
 必需。  `Date` 对象。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。  包含一个或多个指定比较选项的特性的对象。  
  
## 备注  
 从 Internet Explorer 11 开始，`toLocaleDateString` 在内部使用 `Intl.DateTimeFormat` 设置格式化日期，添加对 `locales` 和 `options` 参数的支持。  有关这些参数的详细信息，请参见 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  `locales` 和 `options` 参数在所有的文档模型和浏览器版本中均不支持。  有关详细信息，请参见“要求”部分。  
  
 在 Internet Explorer 10 标准文档模式、早期文档模式和突发模式下使用 `toLocaleDateString` 时：  
  
-   它返回包含当前时区中某个日期的字符串值。  
  
-   所返回日期采用宿主环境当前区域设置的默认格式。  
  
 如果您省略了 `locales` 参数，此方法的返回值将随计算机的不同而不同，因为脚本撰写过程中不能依赖该返回值。  在此方案中，仅使用该方法设置显示文本的格式 \- 请勿在计算过程中使用。  
  
## 示例  
 下面的示例显示如何使用带指定区域设置和比较选项的 `toLocaleDateString` 方法。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toDateString 方法 \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)