---
title: "getYear 方法 (Date) (JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，返回年"
  - "GetYear 方法"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear 方法 (Date) (JavaScript)
获取 `Date` 对象中的年份。  
  
## 语法  
  
```  
  
dateObj.getYear()   
```  
  
#### 参数  
 必需的 `dateObj` 引用 `Date` 对象。  
  
## 返回值  
 返回中。  
  
## 备注  
  
> [!IMPORTANT]
>  此方法已过时以及仅用于向后兼容提供。  请改用 `getFullYear` 方法。  
  
 在 [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]，然后在从开始 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]的Internet Explorer版本，返回的值是递减1900中存储的年份。  例如，1899 年的返回值是 \-1，而 2000 年的返回值是 100。  
  
 在 [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] 通过 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]，公式取决于年。  1900年到1999中，返回的值是递减1900中的存储中的一个2位数值。  对于排列\)的日期外部，四位数字的年份返回。  例如， 1996中返回为96，但是， 1825和2025返回。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Date 对象](../../javascript/reference/date-object-javascript.md)  
  
## 请参阅  
 [getFullYear 方法 \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear 方法 \(Date\)](../../javascript/reference/setyear-method-date-javascript.md)