---
title: "如何： 打开标准编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd3e3b8da06e6846c8c6adc6ddc3f65873c1e2bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-standard-editors"></a>如何： 打开标准编辑器
标准编辑器打开时，你将让 IDE 确定指定的文件类型，而不是指定的文件的项目特定编辑器的标准编辑器。  
  
 完成以下过程来实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 这将在标准编辑器中打开项目文件。  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>若要使用标准编辑器实现 OpenItem 方法  
  
1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) 来确定文档数据对象文件是否已打开。  
  
2.  如果文件已打开，通过调用 resurface 文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法，将值指定为`IDO_ActivateIfOpen`为`grfIDO`参数。  
  
     如果文件处于打开状态，并且该文档拥有的不同于调用项目的项目，你的项目将接收所打开的编辑器处于另一个项目中的警告。 然后显示文件窗口。  
  
3.  如果文档未打开或正在运行的文档表中没有调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法 (`OSE_ChooseBestStdEditor`) 以打开该文件的标准编辑器。  
  
     在调用方法时，IDE 将执行以下任务：  
  
    1.  IDE 将扫描编辑器 / {guidEditorType} / 注册表项以确定哪种编辑器中的扩展子项可以打开的文件，并具有执行此操作的最高优先级。  
  
    2.  IDE 已确定哪种编辑器可以打开的文件后，IDE 会调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。 此方法的编辑器的实现返回所需 ide 调用信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>和站点新打开的文档。  
  
    3.  最后，通过使用常用的持久性接口，如加载 IDE 文档<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>。  
  
    4.  如果 IDE 以前已确定层次结构或层次结构项是否可用，IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>项目获取项目级别上下文方法<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指针，用以传递中并返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法调用。  
  
4.  返回<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指向 IDE 时 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>上你项目中，如果你想要允许从你的项目的编辑器 get 上下文。  
  
     执行此步骤允许到编辑器项目提供其他服务。  
  
     如果在一个窗口框架中，成功放置文档视图或文档视图对象，该对象初始化与它的数据通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 打开项目特定编辑器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何： 打开编辑器的打开的文档](../extensibility/how-to-open-editors-for-open-documents.md)   
 [使用“打开文件”命令显示文件](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)