---
title: "getDay 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay 方法"
  - "Date 对象"
  - "日期，返回星期几"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay 方法 (Date) (JavaScript)
使用当地时间获取星期数。  
  
## 语法  
  
```  
  
dateObj. getDay()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 一个介于 0 和 6 之间的整数，该整数表示星期数（0 表示周日，6 表示周六）。  
  
## 备注  
 若要使用协调通用时间 \(UTC\) 获取天数，请使用 `getUTCDay` 方法。  
  
 下面的示例演示如何使用 `getDay` 方法。  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCDay 方法 \(Date\)](../../javascript/reference/getutcday-method-date-javascript.md)