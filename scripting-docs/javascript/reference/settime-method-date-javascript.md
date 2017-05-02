---
title: "setTime 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime 方法"
  - "时间方法"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime 方法 (Date) (JavaScript)
设置 `Date` 对象中的日期和时间值。  
  
## 语法  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## 参数  
 `dateObj`  
 必需。  任意 `Date` 对象。  
  
 *milliseconds*  
 必需。  一个数值，表示自 GMT 1970 年 1 月 1 日午夜之后经过的毫秒数。  
  
## 备注  
 如果 *milliseconds* 是一个负值，则它表示 1970 年之前的日期。  可用的日期范围大约是 1970 年前后的 285,616 年。  
  
 使用 `setTime` 方法对日期和时间所进行的设置与时区无关。  
  
## 示例  
 下面的示例阐释了 `setTime` 方法的用法。  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getTime 方法 \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)