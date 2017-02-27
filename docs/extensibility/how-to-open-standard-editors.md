---
title: "如何: 打开标准编辑器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "打开编辑器 [Visual Studio SDK]"
  - "项目 [Visual Studio SDK]，打开标准编辑器"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何: 打开标准编辑器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当您打开一个标准编辑时，将使 IDE 确定一指定的文件类型的标准编辑，而不是指定一个项目特定版本的文件。  
  
 完成以下过程执行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法。  这将打开在标准编辑的项目文件。  
  
### 执行与标准编辑的 OpenItem 方法  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) 确定文档数据对象文件是否已打开。  
  
2.  如果该文件已经处于打开状态，请通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法复出文件，指定 `IDO_ActivateIfOpen` 的值。 `grfIDO` 参数。  
  
     如果文件已打开，并且文档由不同的项目与该调用项目所拥有，该项目会收到中打开的编辑器是从另一个项目的警告。  文档窗口然后图面。  
  
3.  如果文档不是打开的或不在运行文档表，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法 \(`OSE_ChooseBestStdEditor`\) 打开文件的标准编辑。  
  
     当您调用方法时， IDE 执行以下任务:  
  
    1.  IDE 浏览注册表中编辑 guidEditorType {} \/Extensions 子项确定要可编辑打开文件并具有最高优先级别实现这一点。  
  
    2.  在 IDE 确定后要可编辑打开文件， IDE 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  此方法的编辑实现返回对于 IDE 所需的调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> ，并放置新打开文档的信息。  
  
    3.  最后，通过使用常用的持久性接口，如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>， IDE 将文档加载。  
  
    4.  如果 IDE 以前确定层次结构或层次结构项可用，则 IDE 缩放在项可以访问的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 方法项目级别上下文 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 指针传递具有 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 方法调用。  
  
4.  返回 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 指向 IDE，当 IDE 调用在项目中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> ，如果要允许从项目中编辑获取上下文。  
  
     执行此步骤允许项提供附加服务到编辑器。  
  
     如果文档视图或在窗架文档视图对象成功已经放置，对象初始化与其数据通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 打开特定于项目的编辑器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 打开编辑器，打开的文档](../extensibility/how-to-open-editors-for-open-documents.md)   
 [通过使用打开文件命令显示文件](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)