---
title: "关于异常的疑难解答：System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException 异常"
  - "AccessViolationException 类"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.AccessViolationException
当尝试读或写受保护的内存时会引发 <xref:System.AccessViolationException>。  
  
## 相关提示  
 确保您尝试访问的内存已分配。  
 自动内存管理是公共语言运行时提供的服务之一。 您可能希望移至托管代码以便利用此服务。 有关详细信息，请参阅[自动内存管理](../Topic/Automatic%20Memory%20Management.md)。  
  
 确保您尝试访问的内存未损坏。  
 如果多次读或写操作时都遇到无效指针，则内存可能已损坏。  
  
### 备注  
 如果非托管代码或不安全代码尝试对尚未分配的或不具有访问权限的内存进行读操作或写操作，就会发生访问冲突。 并非所有通过无效指针的读或写操作都会导致访问冲突，所以访问冲突通常指示已经通过无效指针进行多次读或写操作，并且内存内容可能已损坏。  
  
 在托管代码中，所有的引用或者有效或者为 null。 尝试在可验证代码中引用 null 引用的任何操作都将引发 <xref:System.NullReferenceException>。  
  
 根据平台不同，不安全的托管代码中发生的访问冲突可以表示为 <xref:System.NullReferenceException> 或 <xref:System.AccessViolationException>。  
  
 向上冒泡到托管代码的非托管代码中的访问冲突总是包装在 <xref:System.AccessViolationException> 中。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [内存管理：示例](../Topic/Memory%20Management:%20Examples.md)   
 [自动内存管理](../Topic/Automatic%20Memory%20Management.md)