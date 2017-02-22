---
title: "如何: 打开特定于项目的编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目类型中，打开特定于项目的编辑器"
  - "编辑器 [Visual Studio SDK]，打开特定于项目的编辑器"
  - "项目 [Visual Studio SDK]，打开文件夹"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 打开特定于项目的编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果项目中打开的项目文件进行内部绑定到该项的特定编辑器中，使用一个项目特定版本，项目必须打开文件。  文件无法将委托滚动到选定的编辑 IDE 的结构。  例如，而不是使用标准的位图编辑器，可以使用此项目特定的编辑器选项指定识别文件中的信息对项目是唯一的特定位图编辑器。  
  
 IDE 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法，则认为应由特定项目中打开文件。  有关更多信息，请参见 [通过使用打开文件命令显示文件](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。  使用一个项目特定的编辑器中，使用以下准则执行 `OpenItem` 方法具有项目中打开文件。  
  
### 执行与一个项目特定版本的 OpenItem 方法  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 方法 \(RDT\_EditLock\) 确定文件 \(文档数据对象\) 是否已打开。  
  
    > [!NOTE]
    >  有关的更多信息文档数据并记录视图对象，请参见 [文档数据和自定义编辑器中的文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)。  
  
2.  如果该文件已经处于打开状态，请通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法并指定 IDO\_ActivateIfOpen 的值复出文件 `grfIDO` 参数的。  
  
     如果文件处于打开状态而不是调用项之外，并且，文档由项目拥有，警告将显示对打开的编辑器是另一个项目的用户。  文档窗口然后图面。  
  
3.  如果文本缓冲区 \(文档数据对象\) 已打开和要附加另一个视图更改为，则负责挂钩该视图。  在运行时实例化一个视图的建议方法 \(文档视图对象\) 从项目，如下所示:  
  
    1.  缩放在 <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> 服务访问的 `QueryService` 指向 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 接口。  
  
    2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 方法创建文档视图类的实例。  
  
4.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 方法，指定文档视图对象。  
  
     此方法放置在文档窗口的文档视图对象。  
  
5.  执行相应的调用 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 方法。  
  
     此时，应完全初始化视图和准备中打开。  
  
6.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法显示和打开视图。  
  
## 请参阅  
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 打开标准编辑器](../extensibility/how-to-open-standard-editors.md)   
 [如何: 打开编辑器，打开的文档](../extensibility/how-to-open-editors-for-open-documents.md)