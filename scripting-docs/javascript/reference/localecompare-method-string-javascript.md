---
title: "localeCompare 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare 方法"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare 方法 (String) (JavaScript)
确定两个字符串在当前区域设置中是否相等。  
  
## 语法  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## 参数  
 `stringVar`  
 必需。  要比较的第一个字符串。  
  
 `stringExp`  
 必需。  要比较的第二个字符串。  
  
 `locales`  
 可选。  包含一种或多种语言或区域设置标记的区域设置字符串数组。  如果包含多个区域设置字符串，请以降序优先级对它们进行排列，确保首个条目为首选区域位置。  如果省略此参数，则使用 JavaScript 运行时的默认区域设置。  此参数必须符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 标准；请参见 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)了解详细信息。  
  
 `options`  
 可选。  包含指定比较选项的一个或多个特性的对象。请参见 [Intl.Collator 对象](../../javascript/reference/intl-collator-object-javascript.md)了解详细信息。  
  
## 备注  
 对于比较字符串，可以指定 `String` 对象或字符串文本。  
  
 从 Internet Explorer 11 开始，`localeCompare` 在内部使用 `Intl.Collator` 对象进行比较，添加对 `locales` 和 `options` 参数的支持。  有关这些参数的详细信息，请参见 [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) 和 [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md)。  
  
> [!IMPORTANT]
>  `locales` 和 `options` 参数在所有的文档模型和浏览器版本中均不支持。  有关详细信息，请参见“要求”部分。  
  
 `localeCompare` 方法对 `stringVar` 和 `stringExp` 执行区分区域设置的字符串比较，并返回以下结果之一，这取决于系统默认区域设置的排序顺序：  
  
-   \-1，如果 `stringVar` 排在 `stringExp` 之前。  
  
-   \+1，如果 `stringVar` 排在 `stringExp` 的后面。  
  
-   如果两个字符串相等，则为 0（零）。  
  
## 示例  
 下面的代码演示如何使用 `localeCompare`。  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## 示例  
 下面的代码显示如何使用具有德语（德国）区域设置的 `localeCompare`。  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## 示例  
 下面的示例显示如何使用具有德语（德国）区域设置和指定德语电话簿排序顺序的区域设置特定扩展的 `localeCompare`。  此示例演示了特定于区域设置的差异。  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 参数：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [toLocaleString 方法 \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)