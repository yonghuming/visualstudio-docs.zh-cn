---
title: "在自定义编辑器中查看文档数据和文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab3506a6906c4223888a14132339cbe5499c92d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>文档数据和自定义编辑器中的文档视图
自定义编辑器由两部分组成： 文档数据对象和文档视图对象。 顾名思义，文档数据对象表示要显示的文本数据，文档视图对象 （或"视图"） 表示要在其中显示文档数据对象的一个或多个 windows。  
  
## <a name="document-data-object"></a>文档数据对象  
 文档数据对象是文本的数据的表示形式的文本缓冲区中。 它是 COM 对象，将文档文本和其他信息存储、 处理文档持久性，并使其数据的多个视图。 有关详细信息，请参见  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>和[文档窗口](../extensibility/internals/document-windows.md)。  
  
 自定义编辑器和设计器可以选择使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象或其自己自定义的缓冲区。 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>为标准编辑器遵循简化的嵌入模型、 支持多个视图，并提供用于管理多个视图的事件接口。  
  
## <a name="document-view-object"></a>文档视图对象  
 一个窗口，显示代码及其他文本被称为文档视图。 当你创建一个编辑器时，你可以选择单个视图中，在单个窗口中，显示文本或多个视图，多个窗口中显示文本。 你的选择取决于你的应用程序。 例如，如果你需要通过并行编辑，你可以选择多个视图。 每个视图都在集成的开发环境的 (IDE) 运行 document 表 (RDT) 的条目相关联。 查看 windows 属于项目或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>对象。  
  
 如果你的编辑器支持文档数据对象的多个视图，你的文档数据和文档视图对象必须单独。 否则，可以将它们分组在一起。 有关详细信息，请参阅[支持多个文档视图](../extensibility/supporting-multiple-document-views.md)。  
  
 IDE 通知通过匹配的项标识符 (ItemID) 正在运行的文档表中每个项的视图获取有关事件 （例如，关闭包含文档的解决方案时）。 有关这方面的详细信息，请参阅[运行 Document 表](../extensibility/internals/running-document-table.md)。  
  
 有两个选项的自定义编辑器中创建视图。 之一是就地激活模型，该视图在窗口中使用 ActiveX 控件或文档数据对象的托管位置。 第二个是简化的嵌入模型，该视图都由[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>实现以处理窗口命令。 有关就地激活模型的信息，请参阅[就地激活](../extensibility/in-place-activation.md)。 简化的嵌入模型有关的信息，请参阅[简化嵌入](../extensibility/simplified-embedding.md)。  
  
## <a name="see-also"></a>另请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [简化嵌入](../extensibility/simplified-embedding.md)   
 [如何： 附加文档数据的视图](../extensibility/how-to-attach-views-to-document-data.md)   
 [文档锁定持有者管理](../extensibility/document-lock-holder-management.md)   
 [单个和多选项卡的视图](../extensibility/single-and-multi-tab-views.md)   
 [保存标准文档](../extensibility/internals/saving-a-standard-document.md)   
 [持久性和运行文档表](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [确定编辑器打开一个项目中的文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [编辑器工厂](../extensibility/editor-factories.md)