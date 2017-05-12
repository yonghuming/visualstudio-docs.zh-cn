---
title: "join 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join 方法"
  - "串联字符串，join 方法"
  - "数组 [Visual Studio]，联接"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join 方法 (Array) (JavaScript)
添加由指定分隔符字符串分隔的数组的所有元素。  
  
## 语法  
  
```  
  
arrayObj.join([separator])   
```  
  
## 参数  
 `arrayObj`  
 必需。  一个 `Array` 对象。  
  
 `separator`  
 可选。  用于将在结果 `String` 中的数组的一个元素与下一个元素分开的字符串。  若忽略此参数，则数组元素之间用逗号分隔。  
  
## 备注  
 如果数组的任一元素为 **undefined** 或 `null`，则该元素将被视为空字符串。  
  
## 示例  
 下面的示例阐释了 **join** 方法的用法。  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)