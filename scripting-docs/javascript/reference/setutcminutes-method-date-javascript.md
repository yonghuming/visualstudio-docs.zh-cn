---
title: "setUTCMinutes 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "分钟"
  - "setUTCMinutes 方法"
  - "UTC 时间, 设置"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes 方法 (Date) (JavaScript)
使用协调通用时间 \(UTC\) 设置 `Date` 对象中的分钟值。  
  
## 语法  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
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
 如果您没有指定可选参数，那么所有采用可选参数的 **set** 方法都将使用相应的 **get** 方法返回的值。  例如，如果未指定 *numSeconds* 参数，则 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 将使用从 `getUTCSeconds` 方法返回的值。  
  
 若要使用当地时间修改分钟值，请使用 `setMinutes` 方法。  
  
 如果参数值大于其范围或为负数，则其他存储的值都将得到相应的修改。  例如，如果所存储的日期是“Jan 5, 1996 00:00:00.00”，并调用了 **setUTCMinutes\(70\)**，则日期将变为“Jan 5, 1996 01:10:00.00”。  
  
 **setUTCHours** 方法可用于设置小时、分钟、秒和毫秒。  
  
## 示例  
 下面的示例阐释了 `setUTCMinutes` 方法的用法：  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMinutes 方法 \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)