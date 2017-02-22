---
title: "如何︰ 附加视图文档数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的视图附加到文档数据"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 附加视图文档数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您有一个新的文档视图，您可能能够将其附加到现有的文档数据对象。  
  
### 若要确定是否可以将视图附加到现有的文档数据对象  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
2.  实现过程中 `IVsEditorFactory::CreateEditorInstance`, ，调用 `QueryInterface` 现有文档的数据对象时 IDE 调用您 `CreateEditorInstance` 实现。  
  
     调用 `QueryInterface` ，您可以检查现有的文档数据对象，后者在中指定 `punkDocDataExisting` 参数。  
  
     确切的接口必须查询，但是，取决于的编辑器中打开该文档，在步骤 4 中所述。  
  
3.  如果找不到现有的文档数据对象上的相应接口，然后将错误代码返回到您，该值指示文档的数据对象与您的编辑器不兼容的编辑器。  
  
     在 IDE 的实现中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, ，一个消息框会通知您，文档在另一个编辑器中打开，并且询问您是否要将其关闭。  
  
4.  如果关闭此文档，然后 Visual Studio 会调用编辑器工厂进行第二次。 在此调用时， `DocDataExisting` 参数是否等于 NULL。 编辑器工厂实现然后可以在您自己的编辑器中打开的文档数据对象。  
  
    > [!NOTE]
    >  若要确定是否可以使用现有的文档数据对象，您还可以使用该接口实现私有知识通过强制转换为实际的指针 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 私有实现的类。 例如，所有的标准编辑器实现 `IVsPersistFileFormat`, ，它是从 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>。 因此，您可以调用 `QueryInterface` 为 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, ，现有的文档的数据对象的类 ID 是否与您的实现匹配和类 ID，则您可以使用文档数据对象。  
  
## 可靠编程  
 当 Visual Studio 会调用您的实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 方法，它返回将指针传递给现有的文档数据对象中 `punkDocDataExisting` 参数，如果存在。 检查文档数据对象中返回 `punkDocDataExisting` 以确定文档数据对象是否适合于您的编辑器中请注意，在本主题中的过程的步骤 4 中所述。 如果合适，则编辑器工厂应提供第二个视图的数据中所述 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。 如果没有，则它应显示相应的错误消息。  
  
## 请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [文档数据和自定义编辑器中的文档视图](../extensibility/document-data-and-document-view-in-custom-editors.md)