---
title: "setUTCDate 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, 设置"
  - "日期, UTC"
  - "setUTCDate 方法"
  - "UTC 日期, 设置"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate 方法 (Date) (JavaScript)
使用协调世界时 \(UTC\) 设置 `Date` 对象中的月日期数值。  
  
## 语法  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 *numDate*  
 必需。  一个表示一个月中某一日的数值。  
  
## 备注  
 若要使用当地时间设置一个月第几天，请使用 `setDate` 方法。  
  
 如果 *numDate* 的值大于 **Date** 对象中所存储的月份中的天数或为负数，那么日期将被设置为由 *numDate* 减去所存储月份中天数而得到的日期。  例如，如果所存储的日期是“1996 年 1 月 5 日”，并且调用了 **setUTCDate\(32\)**，则日期将更改为“1996 年 2 月 1 日”。  负数的处理方法与此相似。  
  
 **setUTCFullYear** 方法可用于设置年、月、日。  
  
## 示例  
 下面的示例阐释了 `setUTCDate` 方法的用法。  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate 方法 \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)