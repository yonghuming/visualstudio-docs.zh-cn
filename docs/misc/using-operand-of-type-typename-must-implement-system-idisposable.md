---
title: "“&lt;typename&gt;”类型的“Using”操作数必须实现 System.IDisposable | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;typename&gt;”类型的“Using”操作数必须实现 System.IDisposable
`Using` 语句指定类型中不实现 <xref:System.IDisposable> 接口的资源。  
  
 `Using` 块用于保证在退出块时释放系统资源。 为满足此目的，资源必须公开从 <xref:System.IDisposable> 实现的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 **错误 ID：**BC36010  
  
### 更正此错误  
  
-   从 `Using` 语句的资源列表中删除此资源，或将其替换为实现 <xref:System.IDisposable> 的资源。  
  
## 请参阅  
 <xref:System.IDisposable>   
 [Using 语句](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [如何：释放系统资源](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)