---
title: "如何： 打开项目特定编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb60f482edeea1271c0f864fd5b907138e83d103
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-project-specific-editors"></a>如何： 打开项目特定编辑器
如果正在打开的项目项文件本质上绑定到该项目的特定编辑器中，项目必须使用特定于项目的编辑器打开文件。 该文件不能被委派到 IDE 的机制，用于选择一个编辑器。 例如，而不是使用标准的位图编辑器，你可以使用此特定项目的编辑器选项以指定一种特定的位图编辑器，识别只出现在你的项目文件中的信息。  
  
 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法确定时，它应由某个特定项目打开文件。 有关详细信息，请参阅[通过使用打开文件命令显示文件](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)。 使用以下准则来实现`OpenItem`方法，让你通过使用特定于项目的编辑器打开文件的项目。  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>若要使用的项目特定编辑器实现 OpenItem 方法  
  
1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法 (RDT_EditLock) 来确定文件 （文档数据对象） 是否已打开。  
  
    > [!NOTE]
    >  有关文档数据和文档视图对象的详细信息，请参阅[文档数据和自定义编辑器中的文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)。  
  
2.  如果文件已打开，通过调用 resurface 文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法并指定一个值为 IDO_ActivateIfOpen`grfIDO`参数。  
  
     如果文件处于打开状态，并且该文档拥有的而不是调用项目的项目，将向正在打开的编辑器是另一个项目中的用户显示一条警告。 然后显示文件窗口。  
  
3.  如果你的文本缓冲区 （文档数据对象） 已打开并且你想要将另一个视图附加到它，你负责挂接该视图。 从项目中，实例化的视图 （文档视图对象） 的建议的方法是，如下所示：  
  
    1.  调用`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>服务以获取指向<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>接口。  
  
    2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>方法来创建文档视图类的实例。  
  
4.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法，指定您的文档视图对象。  
  
     此方法站点在文档窗口中的文档视图对象。  
  
5.  执行适当的调用为<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>方法。  
  
     此时，该视图应是完全初始化并准备要打开。  
  
6.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法以显示和打开该视图。  
  
## <a name="see-also"></a>另请参阅  
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何： 打开标准编辑器](../extensibility/how-to-open-standard-editors.md)   
 [如何：打开开放文档的编辑器](../extensibility/how-to-open-editors-for-open-documents.md)