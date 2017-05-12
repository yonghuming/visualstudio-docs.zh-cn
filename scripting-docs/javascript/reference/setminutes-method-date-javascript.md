---
title: "setMinutes 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分钟"
  - "setMinutes 方法"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes 方法 (Date) (JavaScript)
使用当地时间设置 **Date** 对象中的分钟值。  
  
## 语法  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numMinutes`  
 必需。  一个等于分钟值的数值。  如果使用下列任意参数，则必须提供此参数。  
  
 *numSeconds*  
 可选。  一个等于秒值的数值。  如果使用 `numMilli` 参数，则必须提供此参数。  
  
 `numMilli`  
 可选。  一个等于毫秒值的数值。  
  
## 备注  
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 *numSeconds* 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 `getSeconds` 方法返回的值。  
  
 若要使用协调通用时间 \(UTC\) 设置分钟值，请使用 `setUTCMinutes` 方法。  
  
 如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果所存储的日期是“Jan 5, 1996 00:00:00”，并调用了 **setMinutes\(90\)**，则日期将变为“Jan 5, 1996 01:30:00”。负数的处理方法与此相似。  
  
## 示例  
 下面的示例阐释了 `setMinutes` 方法的用法。  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMinutes 方法 \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)