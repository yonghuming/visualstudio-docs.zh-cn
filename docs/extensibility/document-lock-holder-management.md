---
title: "文档锁定持有者管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4bd487bd3f5a6978af9f79eb9e0a00866b5df52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="document-lock-holder-management"></a>文档锁定持有者管理
正在运行的文档表 (RDT) 维护打开的文档和它们具有任何编辑锁的计数。 以编程方式编辑在后台，而用户看到在文档窗口中的打开文档时，可以放 RDT 中的文档的编辑锁。 修改通过图形用户界面的多个文件的设计器经常使用此功能。  
  
## <a name="document-lock-holder-scenarios"></a>文档锁定持有者方案  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>文件"a"具有对文件的依赖项"b"  
 考虑实现文件类型的标准编辑器"A"的其中一种情况"a"和"a"具有对引用 （或依赖于） 的类型的每个文件类型"b"的文件。 标准编辑器"B"类型"b"的文件存在。 当编辑器"A"打开文件"a"，则将检索到相应的文件"b"的引用。 不显示文件"b"，但编辑器"A"可以对其进行修改。 编辑器"A"获取对文件的文档数据的引用"b"从<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法并保留文件"b"上的编辑锁。 编辑器"A"完成后修改文件"b"可以递减编辑锁数将文件"b"上调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法。 如果已调用，则可以忽略此步骤<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>与参数的方法`dwRDTLockType`设置为<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>其他编辑器打开文件"b"  
 中，当尝试打开该编辑器"A"编辑器"B"已打开文件"b"，有两个单独的方案来处理：  
  
-   如果在兼容的编辑器中打开文件"b"，你必须具有编辑器"A"注册"b"文件使用的文档编辑锁<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法。 文档中取消注册你的编辑器"A"完成修改文件"b"后，编辑锁使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>方法。  
  
-   如果在一种不兼容的方法中打开文件"b"，你可以通过"A"出现故障后，也可以让与编辑器"A"部分打开并显示相应的错误消息关联的视图的编辑器让尝试的打开文件"b"。 错误消息应指示用户关闭不兼容的编辑器中的文件"b"，然后重新打开文件"a"使用编辑器"A"。 你也可以实现[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>提示用户关闭文件"b"不兼容的编辑器中打开。 如果用户关闭文件"b"，打开文件"a"中的编辑器"A"将继续正常进行。  
  
## <a name="additional-document-edit-lock-considerations"></a>其他文档编辑锁注意事项  
 如果编辑器"A"是都具有编辑锁定文件"b"比"B"编辑器还包含文档的文档仅编辑器编辑文件"b"上的锁，获取不同的行为。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，**类设计器**是可视化设计器中，不保存的编辑锁上关联的代码文件的示例。 也就是说，如果用户具有在设计视图中打开类关系图并同时打开关联的代码文件时，如果用户修改的代码文件，但不保存所做的更改，所做的更改也将丢失到类图 (.cd) 文件。 如果**类设计器**具有唯一的文档编辑代码文件上的锁，则不要求用户以保存所做的更改，关闭代码文件时。 IDE 将要求用户将保存所做的更改，用户关闭后仅**类设计器**。 已保存的更改会反映在这两个文件。 如果这两个**类设计器**和代码文件编辑器代码文件中上, 保留文档编辑锁，则系统会提示用户保存时关闭该代码文件或窗体。 此时，已保存的更改会反映在窗体和代码文件。 在类图上的详细信息，请参阅[使用类图 （类设计器）](../ide/working-with-class-diagrams-class-designer.md)。  
  
 请注意，是否你需要在非编辑器文档上放置编辑锁定，则必须实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>接口。  
  
 很多时候一个 UI 设计器，以编程方式修改代码文件将对多个文件中做出更改。 在这种情况下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>方法可处理的一个或多个文档的方式保存**你想要将更改保存到以下各项？**对话框。  
  
## <a name="see-also"></a>另请参阅  
 [正在运行的文档表](../extensibility/internals/running-document-table.md)   
 [持久性和正在运行的文档表](../extensibility/internals/persistence-and-the-running-document-table.md)