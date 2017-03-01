---
title: "文档锁持有者管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>文档锁持有者管理
运行文档表 (RDT) 将保持打开的文档和它们拥有的任何编辑锁计数。 以编程方式编辑在后台，而用户看到在文档窗口中打开的文档时，您可以编辑锁放置在文档中 RDT。 修改多个文件通过图形用户界面的设计器经常使用此功能。  
  
## <a name="document-lock-holder-scenarios"></a>文档锁持有者方案  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>文件"a"具有的依赖文件"b"  
 假设您在其中实施文件类型的标准编辑器"A""a"和"a"具有对引用 （或依赖关系） 的类型的每个文件类型"b"的文件。 标准编辑器"B"类型"b"的文件存在。 当打开文件编辑器"A"，其中"a"，则会检索对相应的文件"b"的引用。 不显示文件"b"，但编辑器"A"可以对其进行修改。 编辑器"A"到文件的文档数据的引用"b"从获取<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法并保留在文件"b"上的编辑锁。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> "A"编辑器完成操作后修改文件"b"才能递减编辑锁数将文件"b"上调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 如果已调用，则可以忽略此步骤<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法及参数`dwRDTLockType`设置为<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>不同的编辑器打开文件"b"  
 中，"b"文件已打开编辑器"B"编辑器"A"尝试将其打开时，有两个单独的处理方案︰  
  
-   如果在兼容的编辑器中打开文件"b"，您必须具有编辑器"A"注册"b"文件中使用的文档编辑锁<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 文档中取消注册您的编辑器"A"可修改文件"b"后，编辑锁使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   如果在一种不兼容的方法中打开文件"b"，你可以通过"A"出现故障，或者您可以让关联的编辑器"A"部分打开并显示相应的错误消息视图编辑器让尝试的打开文件"b"。 错误消息应指示用户在不兼容的编辑器中关闭文件"b"，然后重新打开"a"使用文件编辑器"A"。 您还可以实现[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>以提示用户关闭文件"b"不兼容的编辑器中打开。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 如果用户关闭文件"b"，打开文件"a"中编辑器"A"将继续正常进行。  
  
## <a name="additional-document-edit-lock-considerations"></a>其他文档编辑锁注意事项  
 如果编辑器"A"是仅具有编辑文件"b"上的锁不是如果编辑器"B"还包含一个文档的文档的编辑器编辑文件"b"上的锁，获得不同的行为。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，**类设计器**是不保持关联的代码文件的编辑锁的可视化设计器的一个示例。 也就是说，如果用户已在设计视图中打开一个类关系图关联的代码文件同时并打开，并且用户可修改的代码文件，但不会保存所做的更改，所做的更改也会丢失到类图 (.cd) 文件。 如果**类设计器**具有唯一的文档编辑的代码文件上的锁，则不要求用户以保存所做的更改，关闭代码文件时。 IDE 将询问用户要保存所做的更改，仅在用户关闭后**类设计器**。 已保存的更改将反映在这两个文件。 如果两个**类设计器**和代码文件编辑器中对代码文件中，则提示用户保存的代码文件或窗体在关闭时所持有文档编辑锁定。 此时，已保存的更改将反映在该窗体和代码文件。 类关系图的详细信息，请参阅[使用类图 （类设计器）](../ide/working-with-class-diagrams-class-designer.md)。  
  
 请注意，是否您需要以将编辑锁置于文档以供非编辑器，您必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 很多时候 UI 设计人员以编程方式修改代码文件对多个文件进行更改。 在这种情况下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>方法可处理的一个或多个文档通过保存**您想要将更改保存到以下各项？**对话框。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>另请参阅  
 [正在运行的 Document 表](../extensibility/internals/running-document-table.md)   
 [持久性和运行 Document 表](../extensibility/internals/persistence-and-the-running-document-table.md)
