---
title: "setMilliseconds 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "setMilliseconds 方法"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds 方法 (Date) (JavaScript)
使用当地时间设置 `Date` 对象中的毫秒值。  
  
## 语法  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 `numMilli`  
 必需。  一个等于毫秒值的数值。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 设置毫秒值，请使用 `setUTCMilliseconds` 方法。  
  
 如果 `numMilli` 的值大于 999 或为负，则所存储的秒数（以及分钟、小时等，如有必要）将增加适当的数量。  
  
## 示例  
 下面的示例阐释了 `setMilliseconds` 方法的用法。  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getMilliseconds 方法 \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)