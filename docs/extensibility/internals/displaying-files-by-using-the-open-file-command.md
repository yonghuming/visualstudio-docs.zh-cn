---
title: "通过使用打开文件命令显示文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目类型中，支持打开的文件命令"
  - "“打开文件”命令"
  - "持久性、 支持打开的文件命令"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 通过使用打开文件命令显示文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列步骤描述 IDE 处理 **打开文件** 命令，可在 **文件** 菜单中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  步骤还介绍源自此命令的项目应如何响应调用。  
  
 当用户在 **文件** 菜单中单击 **打开文件** 命令，然后选择文件从 **打开文件** 对话框时，以下过程发生。  
  
1.  使用运行文档表， IDE 确定文件是否已在中打开项目。  
  
    -   如果文件处于打开状态， IDE 复出窗口。  
  
    -   如果文件不是打开的， IDE 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 查询每个项目确定哪个项目可以打开文件。  
  
        > [!NOTE]
        >  在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>的项目实现，请提供指示级别打开该项目文件的一个优先级值。  优先级值在 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 枚举提供。  
  
2.  每个项目响应以及指示重要性它在将打开文件的项的优先级别。  
  
3.  IDE 使用以下条件确定哪个项目打开文件:  
  
    -   响应具有最高优先级的项 \(DP\_Intrinsic\) 打开文件。  如果多个项目响应按以下优先级，响应的第一个项目打开文件。  
  
    -   如果项目不响应具有最高优先级 \(DP\_Intrinsic\)，但是，所有项目响应具有相同，更低优先级，事件项目中打开文件。  如果项目不处于活动状态，响应的第一个项目打开文件。  
  
    -   如果项目不要求文件 \(DP\_Unsupported\) 的所有权，杂项文件项目中打开文件。  
  
         如果杂项文件项目创建一个实例，该项目始终响应与该值 DP\_CanAddAsExternal。  此值指示该项可以打开文件。  此项目用于将未在其他项目中打开文件。  项列表在此项目中不会保留;，并且只用于打开文件时，此项目是显示在 **解决方案资源管理器** 。  
  
         如果杂项文件项目不指示它可以打开文件，则项目的实例未创建。  在这种情况下， IDE 会创建杂项文件项目的实例并调用项目中打开文件。  
  
4.  当 IDE 确定哪个项目打开文件，它对该项目的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法。  
  
5.  该项目并具有打开文件的选项使用一个项目特定版本或标准编辑。  有关更多信息，请分别参见 [如何: 打开特定于项目的编辑器](../../extensibility/how-to-open-project-specific-editors.md)和[如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)。  
  
## 请参阅  
 [通过使用命令打开显示文件](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 打开特定于项目的编辑器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 打开标准编辑器](../../extensibility/how-to-open-standard-editors.md)