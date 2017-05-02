---
title: "字符集范围无效 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 字符集范围无效 (JavaScript)
尝试使用无效字符集范围创建正则表达式。  字符集必须仅包含字符（如 a\-z 或 0\-9）；无法在字符集中包含字符类（如 \\w）。  此外，范围内的第一个字符必须在范围内的第二个字符的前面。  例如：  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### 更正此错误  
  
-   仅使用单一字符组成正则表达式的字符集，并确保其顺序正确。  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)