---
title: "source 属性（正则表达式）(JavaScript) | Microsoft Docs"
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
  - "source"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Source 属性"
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# source 属性（正则表达式）(JavaScript)
返回正则表达式模式的文本的一个副本。  只读。  `rgExp` 参数是一个 **Regular Expression** 对象。  它可以是变量名或文本。  
  
## 语法  
  
```  
  
rgExp.source  
```  
  
## 示例  
 下面的示例阐释了 **source** 属性的用法：  
  
```javascript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**：[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)