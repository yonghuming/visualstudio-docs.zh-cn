---
title: "如何: 打开编辑器，打开的文档 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，打开要执行打开的文档"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何: 打开编辑器，打开的文档
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在项目打开文档窗口之前，该项目必须首先确定文件是否已已在其他编辑器中文档窗口。  文件将在一个项目特定版本或一个标准编辑器中打开到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]注册。  
  
## 打开一个项目特定版本  
 使用以下过程打开已打开的文件的一个项目特定版本。  
  
#### 打开打开文件的一个项目特定版本  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。  
  
     此调用返回指向文档的层次结构、层次结构项目和窗口框架组成，通常，如果适用\)。  
  
2.  如果文档处于打开状态，该项目必须检查仅在文档数据对象是否存在，或者，如果文档视图对象还存在。  
  
    -   如果文档视图对象存在，因此，此视图是一个不同的层次结构或层次结构项目，该项目使用指针到视图的窗架复出现有窗口。  
  
    -   如果文档视图对象存在，因此，此视图是为同一个层次结构和层次结构项目，该项目可以打开第二个视图，则可以附加到基础文档数据对象。  否则，该项目应使用指针到视图的窗架复出现有窗口。  
  
    -   如果只有文档数据对象存在，该项目应确定它是否可以为其视图使用文档数据对象。  如果文档数据对象是兼容的，请完成 [打开一个项目特定版本](../extensibility/how-to-open-project-specific-editors.md)讨论的步骤。  
  
     如果文档数据对象不兼容，则应将错误以指示的用户文件当前正在使用的。  除了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心文本编辑器时，，那么，当文件编译用户同时尝试打开文件使用编辑器在临时情况应该只显示此错误，如。  核心文本编辑器可以共享文档与编译器的数据对象。  
  
3.  如果文档尚未打开，因为没有文档数据对象或文档视图对象，在 [打开一个项目特定版本](../extensibility/how-to-open-project-specific-editors.md)的步骤。  
  
## 打开标准编辑  
 使用以下过程打开已打开的文件的标准编辑。  
  
#### 打开打开文件的标准编辑  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
     此方法首先验证文档通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>尚未打开的。  如果文档已打开的，则其编辑器窗口复出。  
  
2.  如果文档尚未打开，然后在完成 [如何: 打开标准编辑器](../extensibility/how-to-open-standard-editors.md)的步骤。  
  
## 请参阅  
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 打开特定于项目的编辑器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 打开标准编辑器](../extensibility/how-to-open-standard-editors.md)