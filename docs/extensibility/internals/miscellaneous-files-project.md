---
title: "杂项文件项目 | Microsoft Docs"
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
  - "向解决方案添加现有文件的文件"
  - "杂项文件项目"
  - "解决方案项目文件夹"
  - "文件，打开与杂项文件项目"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 杂项文件项目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当用户打开项目项时， IDE 分配给杂项文件项目不是任何项目的成员在解决方案中的所有项目。  
  
 投影效果。确定要使用的重大影响编辑器，当用户打开项目项时。  使用一个项目特定版本或标准编辑器中，项目都可以设计打开某些文件。  
  
 一个项目特定版本通常需要用户特定知识或从项目中使用特定接口。  有关更多信息，请参见 [如何: 打开特定于项目的编辑器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
 标准的可编辑打开某个特定扩展名的所有文件在任何项目的。  用户可以自定义一些标准编辑器，如 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 文本编辑器中，对于此类情况，项，但仍保留它们的公共字符。  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，标准编辑器中创建。  
  
 如果在解决方案中的项目不响应它可以打开项目项， IDE 提供调用打开所有文件的杂项文件项目的特定项。  
  
 此特定项目提供打开位于项目的上下文之外的文件。  在处理 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 方法中，杂项文件项目始终响应与一个非常低优先级。  因此，杂项文件始终项目将会打开文件的所有较高优先级的项。  
  
 杂项文件项目不要求用户在 **新项目** 对话框显式创建它。  此外，杂项文件项目不永久管理项目成员列表。  它使用可选功能来跟踪每个用户的最近使用的文件的列表。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [如何: 打开特定于项目的编辑器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)