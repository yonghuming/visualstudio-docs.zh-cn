---
title: "管理撤消和重做通过使用旧 API | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的撤消管理"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 管理撤消和重做通过使用旧 API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

编辑器必须支持使用户可以撤消他们最近的更改时它们修改代码的撤消操作。 在实现大多数编辑器 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 可以撤消支持自动提供的集成的开发环境 \(IDE\)。  
  
## 本节内容  
 [如何: 实现撤消管理](../extensibility/how-to-implement-undo-management.md)  
 与一个或多个视图的编辑器提供恢复数据的功能。  
  
 [如何: 清除撤消堆栈](../extensibility/how-to-clear-the-undo-stack.md)  
 说明如何清除撤消堆栈。  
  
 [如何: 使用链接的撤消管理](../extensibility/how-to-use-linked-undo-management.md)  
 将链接的撤消管理合并到您的编辑器。  
  
## 参考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供一个编辑器，支持多个视图的撤消管理。  
  
## 相关章节