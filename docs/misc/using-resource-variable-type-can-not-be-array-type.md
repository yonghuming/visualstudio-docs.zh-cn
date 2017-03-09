---
title: "“Using”资源变量类型不能是数组类型 | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Using”资源变量类型不能是数组类型
`Using` 语句指定资源的数组变量。  
  
 <xref:System.Array> 类未实现 <xref:System.IDisposable> 接口，因此 `Using` 块不能在数组资源上调用 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 **错误 ID：**BC36012  
  
### 更正此错误  
  
-   在 `Using` 块中使用不同类型的系统资源。  
  
## 请参阅  
 [Using 语句](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [如何：释放系统资源](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [NOTINBUILD Visual Basic 中的数组概述](http://msdn.microsoft.com/zh-cn/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)