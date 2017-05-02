---
title: "正则表达式中应有“]”(JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 正则表达式中应有“]”(JavaScript)
尝试为正则表达式匹配项创建字符类，但不包括右括号。  可通过将各个文本字符组合放入括号内来将其组合成字符类中。  字符类与其包含的任一字符均匹配。  例如，\/\[abc\]\/ 与“a”、“b”或“c”中的任一字母均匹配。  
  
### 更正此错误  
  
-   将右括号添加到正则表达式。  
  
    > [!NOTE]
    >  如果要与一个中括号匹配，请用反斜杠对其进行转义（即 \\\[），这样 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就不会将其解释为特殊字符。  
  
## 请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-cn/ab0766e1-7037-45ed-aa23-706f58358c0e)