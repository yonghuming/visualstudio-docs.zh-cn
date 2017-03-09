---
title: "关于异常的疑难解答：System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OutOfMemoryException 类"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.OutOfMemoryException
当尝试分配内存失败时，会引发 <xref:System.OutOfMemoryException> 异常。  
  
## 相关提示  
 **如果要创建数组，请确保大小正确。**  
 有关详细信息，Visual Basic 用户可参阅 [数组](/dotnet/visual-basic/programming-guide/language-features/arrays/index)。  
  
 有关详细信息，C\# 用户可参阅[数组](/dotnet/csharp/programming-guide/arrays/index)。  
  
 **确保有足够的内存用于内部用途和新的托管对象。**  
 如果您正在 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 上进行编程，当没有足够的内存可用于内部用途或新的托管对象时，公共语言运行时会引发此异常。 要避免此异常，应避免编写占用 64KB 或更多内存的大方法。  
  
## 备注  
 过多的托管内存使用量通常由以下因素造成：  
  
-   将大型数据集读入内存中。  
  
-   创建过多的缓存条目。  
  
-   上载或下载大文件。  
  
-   在分析文件时过多地使用正则表达式或字符串。  
  
-   过多的视图状态。  
  
-   会话状态中有过多的数据或者会话过多。  
  
 当对 COM 对象调用一个方法，并且该方法返回包含安全数组（大小不固定的数组）的用户定义类型时，可能引发此异常，并附带一条额外的消息“存储空间不足，无法完成此操作”。 这是因为 .NET Framework 无法封送带有安全数组类型的结构字段。  
  
## 请参阅  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)