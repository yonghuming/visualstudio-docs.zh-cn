---
title: "关于异常的疑难解答：System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException 类"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.StrongTypingException
当用户访问强类型 <xref:System.Data.StrongTypingException> 中的 <xref:System.DBNull> 值时，发生 <xref:System.Data.DataTable.DataSet%2A>。  
  
## 相关提示  
 **添加 StrongTypingException 的错误处理。**  
 将访问 <xref:System.Data.DataTable.DataSet%2A> 的代码放置在 `Try…Catch` 块中，并捕捉 <xref:System.Data.StrongTypingException>。  
  
## 请参阅  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally 语句](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [在 Visual Studio 中使用数据集](../data-tools/dataset-tools-in-visual-studio.md)