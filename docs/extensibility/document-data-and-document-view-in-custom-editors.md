---
title: "文档数据和自定义编辑器中的文档视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的文档数据和文档视图"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 文档数据和自定义编辑器中的文档视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

自定义编辑器由两部分组成 ︰ 一个文档数据对象和文档视图对象。 顾名思义，文档数据对象表示要显示的文本数据和文档视图对象 （或"视图"） 表示要在其中显示文档的数据对象的一个或多个窗口。  
  
## 文档数据对象  
 文档数据对象是文本的数据的表示形式的文本缓冲区中。 它是一个 COM 对象，以便存储文档文本和其他信息、 处理文档持久性，并使其数据的多个视图。 有关详细信息，请参见  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> 和 [文档窗口](../extensibility/internals/document-windows.md)。  
  
 自定义编辑器和设计器可以选择使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象或其自己自定义的缓冲区。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 简化的嵌入模型遵循标准编辑器、 支持多个视图，并提供用于管理多个视图的事件接口。  
  
## 文档视图对象  
 一个窗口，显示代码和其他文本被称为文档视图。 当您创建一个编辑器时，可以选择单个视图中，在单个窗口中，显示文本或多个视图中，在多个窗口中显示文本。 您的选择取决于您的应用程序。 例如，如果您需要通过并行编辑，您可以选择多个视图。 每个视图都与集成的开发环境的 \(IDE\) 运行 document 表 \(RDT\) 中的条目相关联。 查看 windows 属于项目或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 对象。  
  
 如果您的编辑器支持文档数据对象的多个视图，您的文档数据和文档视图对象必须单独。 否则，则可以将它们分组在一起。 有关详细信息，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
 IDE 会通过正在运行的 document 表中每个条目匹配的项标识符 \(ItemID\) 通知视图获取有关事件 （例如，关闭一个包含文档的解决方案时）。 有关这方面的更多信息，请参见 [正在运行的 Document 表](../extensibility/internals/running-document-table.md)。  
  
 有两个选项用于自定义编辑器中创建视图。 一个是在就地激活模型，该视图在窗口中使用 ActiveX 控件或文档的数据对象的托管位置。 第二个是简化的嵌入模型，该视图都由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 实现来处理窗口命令。 有关就地激活模型的信息，请参阅 [就地激活](../misc/in-place-activation.md)。 简化的嵌入模型有关的信息，请参阅 [简化的嵌入](../extensibility/simplified-embedding.md)。  
  
## 请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [简化的嵌入](../extensibility/simplified-embedding.md)   
 [如何︰ 附加视图文档数据](../extensibility/how-to-attach-views-to-document-data.md)   
 [文档锁持有者管理](../extensibility/document-lock-holder-management.md)   
 [单个和多选项卡上的视图](../extensibility/single-and-multi-tab-views.md)   
 [保存标准文档](../extensibility/internals/saving-a-standard-document.md)   
 [持久性和运行 Document 表](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [确定哪个编辑器随即打开，在项目中的文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [编辑器工厂](../extensibility/editor-factories.md)