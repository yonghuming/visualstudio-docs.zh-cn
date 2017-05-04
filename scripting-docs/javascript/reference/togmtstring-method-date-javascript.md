---
title: "toGMTString 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString 方法"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString 方法 (Date) (JavaScript)
返回使用格林尼治标准时间 \(GMT\) 转换为字符串的日期。  
  
## 语法  
  
```  
  
dateObj.toGMTString()   
```  
  
## 备注  
 必需的 `dateObj` 引用是任何 `Date` 对象。  
  
 `toGMTString` 方法已经过时，之所以仍然提供这个方法，只是为了向后兼容。  推荐改用 `toUTCString` 方法。  
  
 `toGMTString` 方法返回一个 `String` 对象，此对象中包含 GMT 惯例格式的日期。  返回值的格式如下所示：“05 Jan 1996 00:00:00 GMT”。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [toUTCString 方法 \(Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)