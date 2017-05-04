---
title: "setYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear 方法"
  - "Year 方法"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear 方法 (Date) (JavaScript)
设置 `Date` 对象中的年份值。  
  
## 语法  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numYear`  
 必需。  对于 1900 到 1999 年，这是等于年份减去 1900 的数值。  对于该范围以外的日期，这是一个 4 位的数值。  
  
## 备注  
 这个方法已经过时，之所以仍然保留，只是为了向后兼容。  请改用 `setFullYear` 方法。  
  
 若要将 `Date` 对象的年份设置为 1997，请调用 **setYear\(97\)**。  若要将年份设置为 2010，请调用 **setYear\(2010\)**。  最后，若要将年份设置为 0\-99 范围内的某一年，请使用 `setFullYear` 方法。  
  
> [!NOTE]
>  对于 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本 1.0，无论 `numYear` 提供的年份值是多少，`setYear` 使用的值都为该年份值加上 1900。  例如，要将年份设置为 1899，则 `numYear` 参数的值是 \-1，而要将年份设置为 2000，则 `numYear` 参数的值是 100。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getFullYear 方法 \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear 方法 \(Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)