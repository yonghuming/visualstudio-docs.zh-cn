---
title: "valueOf 方法 (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf 方法 (Date)
返回从 UTC 1970 年 1 月 1 日午夜开始的存储的时间值（以毫秒为单位）。  
  
## 语法  
  
```  
  
date.valueOf()  
```  
  
#### 参数  
 `date` 对象是 Date 的任何实例。  
  
## 返回值  
 从 UTC 1970 年 1 月 1 日午夜开始的存储的时间值（以毫秒为单位）。  这是与 `getTime` 相同的值。  
  
## 示例  
 下面的示例阐释了使用日期的 `valueOf` 方法的用法。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]