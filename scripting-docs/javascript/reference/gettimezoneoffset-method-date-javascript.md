---
title: "getTimezoneOffset 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset 方法"
  - "时区 [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset 方法 (Date) (JavaScript)
获取本地计算机的时间与协调通用时间 \(UTC\) 之间的分钟差值。  
  
## 语法  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 返回当前计算机（客户端计算机或服务器计算机（如果从服务器脚本调用此方法））的时间与 UTC 之间的分钟数。  如果当前计算机的本地时间在 UTC 之后（例如太平洋夏时制）则为正值，如果当前计算机的本地时间是 UTC 之前（例如日本）则为负值。  当位于洛杉矶的客户端在 12 月 1 日与位于纽约市的服务器进行联系时，如果是在客户端上执行的，则 `getTimezoneOffset` 返回 480；如果是在服务器上执行的，则它返回 300。  
  
## 备注  
  
## 示例  
 下面的示例演示如何使用 `getTimezoneOffset` 方法。  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getTime 方法 \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)