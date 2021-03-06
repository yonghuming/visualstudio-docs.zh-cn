---
title: "表达式的类型为“&lt;typename&gt;”，该类型不是集合类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 表达式的类型为“&lt;typename&gt;”，该类型不是集合类型
`For Each` 语句中指定的组变量不是集合对象或数组，并且其类型未实现 <xref:System.Collections.IEnumerable> 接口。 此类型必须支持 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 集合设计模式或实现 <xref:System.Collections.IEnumerable>。  
  
 **错误 ID：**BC32023  
  
### 更正此错误  
  
-   将组变量声明为支持 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 集合设计或实现 <xref:System.Collections.IEnumerable> 的类类型。  
  
## 请参阅  
 <xref:System.Collections.IEnumerable>   
 [For Each...Next 语句](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Visual Basic 集合类](http://msdn.microsoft.com/zh-cn/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)