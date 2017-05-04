---
title: "toString 方法（日期） | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString 方法（日期）
返回日期的字符串表示形式。  字符串的格式取决于区域设置。  关于 美.国.英语 \(en\-us\)，按如下所示：  
  
 *周日期* *月* *日* *小时*：*分钟*：*秒* *时区* *年*  
  
## 语法  
  
```  
  
date.toString()  
```  
  
## 参数  
 `date`  
 必需。  要表示为字符串的日期。  
  
## 返回值  
 返回日期的字符串表示形式。  
  
## 示例  
 以下示例阐释了使用日期的 `toString` 方法的用法。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]