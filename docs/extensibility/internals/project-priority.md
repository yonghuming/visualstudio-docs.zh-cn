---
title: "项目优先级 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [Visual Studio SDK]，打开项目"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 项目优先级
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

项目项通常仅在解决方案中的项目的成员。  因此， IDE 会轻易地确定哪个项目用于打开项目。  但是，因此，如果项目是多个项目的成员， IDE 使用优先级架构确定打开的项目最佳项目。  
  
 下面的列表显示项目优先级模式:  
  
-   IDE 对每个项的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 方法将解决方案确定文档是否是该项目的成员。  
  
-   如果文档是项目的成员，项目以响应该项目基于其处理该分配文档的优先级。  例如，语言项目回答 " 是一项资源的语言源文件，但响应具有低优先级不用作其生成过程中未识别的文件类型的。  
  
-   对于文档还提供自定义，项目特定的编辑器或设计器的项目接收高的优先级。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 枚举提供文档优先级值。  
  
-   指定最高优先级给定的项目打开文档的上下文。  如果两个项目返回等于优先级值，活动项目首选方法。  如果在解决方案中的项目不响应它可以打开文档时， IDE 在 " 杂项文件 " 项目将文档。  有关更多信息，请参见 [杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)。  
  
## 请参阅  
 [杂项文件项目](../../extensibility/internals/miscellaneous-files-project.md)   
 [如何: 打开编辑器，打开的文档](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)