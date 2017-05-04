---
title: "getFullYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，返回年"
  - "Date 对象"
  - "getFullYear 方法"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear 方法 (Date) (JavaScript)
使用当地时间获取年份。  
  
## 语法  
  
```  
  
dateObj.getFullYear()   
```  
  
#### 参数  
 必需的 `dateObj` 引用是 `Date` 对象。  
  
## 返回值  
 由四位数字表示的年份。  例如，1976 年的返回值为 1976。  在 `Date` 构造函数或 `setFullYear` 中指定为两位数字的年份被假定处于 20 世纪，因此，对于给定的“5\/14\/12”，`getFullYear` 将返回“1912”。  
  
## 备注  
 若要根据协调世界时 \(UTC\) 获取年份，请使用 `getUTCFullYear` 方法。  
  
## 示例  
 以下示例演示 **getFullYear** 方法的用法。  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getUTCFullYear 方法 \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)