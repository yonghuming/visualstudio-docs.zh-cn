---
title: "&quot;WriteOnly&quot; 属性中不允许出现 XML 注释标记 &quot;returns&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42313"
  - "bc42313"
helpviewer_keywords: 
  - "BC42313"
ms.assetid: 43dca605-187e-4b0b-b29f-5cc4dcdc5f9f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;WriteOnly&quot; 属性中不允许出现 XML 注释标记 &quot;returns&quot;
WriteOnly 属性中不允许有 XML 注释标记 "returns"。 将忽略 XML 注释。  
  
 只写属性声明的 XML 注释不能包含 \<returns\> 标记。  
  
 **错误 ID：**BC42313  
  
### 更正此错误  
  
-   删除不受支持的 \<returns\> 标记。  
  
## 请参阅  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML 注释标记](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [使用 XML 将代码文档化](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Property 语句](/dotnet/visual-basic/language-reference/statements/property-statement)