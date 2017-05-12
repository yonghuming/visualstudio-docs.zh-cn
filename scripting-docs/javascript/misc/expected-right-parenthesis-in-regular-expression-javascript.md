---
title: "正则表达式中应有“)”(JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 正则表达式中应有“)”(JavaScript)
您尝试创建一个正则表达式捕获、断言或组，但不包括右括号。  括号在正则表达式中有多种用途。  它们主要用于捕获子表达式、指定断言或将模式组合在一起，以便通过 \*、\+、？等将项视为一个单元。  
  
### 更正此错误  
  
-   添加最右侧的右括号。  
  
    > [!NOTE]
    >  如果要与一个括号匹配，请用反斜杠对其进行转义（即 \\\(），这样 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就不会将其解释为特殊字符。  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)