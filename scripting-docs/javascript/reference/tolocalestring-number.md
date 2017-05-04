---
title: "toLocaleString (Number) | Microsoft Docs"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
使用当前区域设置或指定的区域设置将数字转换为字符串。  
  
## 语法  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### 参数  
 `numberObj`  
 必需。  要转换的 `Number` 对象。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  
  
 `options`  
 可选。  包含一个或多个指定比较选项的特性的对象。  
  
## 备注  
 开始在 Internet Explorer 11，`toLocaleString`在内部使用 `Intl.NumberFormat` 进行比较，添加对 `locales` 和 `options` 参数支持。  有关这些参数的详细信息，请参见 [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  `locales` 和 `options` 参数在所有的文档模型和浏览器版本中均不支持。  有关详细信息，请参见“要求”部分。  
  
> [!NOTE]
>  如果您忽略 `locales` 参数，请使用 `toLocaleString` 仅向用户显示结果；请勿用其在脚本中计算值，因为返回的结果是计算机特定的（该方法返回当前区域设置）。  
  
## 示例  
 下面的示例显示如何使用无参数的 `toLocaleString` 方法。  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## 示例  
 下面的示例显示如何使用带指定区域设置和比较选项的 `toLocaleString` 方法。  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toLocaleDateString 方法 \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)