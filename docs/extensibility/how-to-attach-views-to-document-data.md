---
title: "如何： 附加文档数据的视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 146303eebbd824342b000fb14b8dbf953c3f0523
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-views-to-document-data"></a>如何： 附加文档数据的视图
如果你有一个新的文档视图，你可能能够将其附加到现有的文档数据对象。  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>若要确定是否可以将视图附加到现有的文档数据对象  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
2.  实现中`IVsEditorFactory::CreateEditorInstance`，调用`QueryInterface`上现有的文档数据对象时 IDE 调用你`CreateEditorInstance`实现。  
  
     调用`QueryInterface`可以检查现有的文档数据对象，它指定在`punkDocDataExisting`参数。  
  
     确切的接口必须查询，但是，取决于的编辑器中打开文档，在步骤 4 中所述。  
  
3.  如果找不到相应的接口上现有的文档数据对象，然后将错误代码返回到你的编辑器，该值指示文档数据对象与你的编辑器不兼容。  
  
     在 IDE 的实现中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，一个消息框会通知你，文档在另一个编辑器中打开，并询问您是否以将其关闭。  
  
4.  如果你关闭此文档，然后 Visual Studio 会调用你的编辑器工厂第二次。 在此调用时，`DocDataExisting`参数等于 NULL。 然后，编辑器工厂实现可以在自己的编辑器中打开文档数据对象。  
  
    > [!NOTE]
    >  若要确定是否可以使用现有的文档数据对象，你还可以使用私有知道接口实现通过强制转换为一个指向实际[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]的私有实现的类。 例如，所有标准编辑器实现`IVsPersistFileFormat`，它继承自<xref:Microsoft.VisualStudio.OLE.Interop.IPersist>。 因此，你可以调用`QueryInterface`为<xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>，并且如果上现有的文档数据对象的类 ID 与匹配你的实现的类 ID，然后你可以使用文档数据对象。  
  
## <a name="robust-programming"></a>可靠编程  
 当 Visual Studio 调用的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，它返回将指针传递给现有的文档数据对象中`punkDocDataExisting`参数，如果存在。 检查文档数据对象中返回`punkDocDataExisting`以确定是否适合你的编辑器，请注意，在本主题中的过程的步骤 4 中所述文档数据对象。 如果合适，则你的编辑器工厂应提供第二个视图的数据中所述[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。 如果没有，然后它应该会显示相应的错误消息。  
  
## <a name="see-also"></a>另请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [自定义编辑器中的文档数据和文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)