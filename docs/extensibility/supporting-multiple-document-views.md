---
title: "支持多个文档视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79b9224a16388dabbe2b68553e5c0d9bfff29519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-document-views"></a>支持多个文档视图
你可以通过为你的编辑器创建单独的文档数据和文档视图对象提供文档的多个的视图。 某些情况下，在此将为有用的附加文档视图是：  
  
-   新窗口支持： 您希望您编辑器来提供相同类型，两个或多个视图，以便已有在编辑器中打开一个窗口的用户可以打开一个新窗口，通过选择**新窗口**命令**窗口**菜单。  
  
-   窗体和代码查看支持： 您希望您编辑器提供了不同类型的视图。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例如，提供窗体视图和代码视图。  
  
 这有关的详细信息，请参阅在 Visual Studio 包模板创建的自定义编辑器项目的 EditorFactory.cs 文件中的 CreateEditorInstance 过程。 有关本项目的详细信息，请参阅[演练： 创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
## <a name="synchronizing-views"></a>同步视图  
 当实现多个视图时，文档数据对象负责保持与数据同步的所有视图。 你可以使用的事件处理接口上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>以多个视图的数据同步的。  
  
 如果不使用<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>同步多个视图，则必须实现自己的事件系统以处理对文档数据对象所做更改的对象。 可以使用不同的粒度级别保持多个视图最新。 利用的最大粒度的设置，在一个视图中键入其他视图立即更新。 最小粒度，与其他视图不会更新之前会激活这些。  
  
## <a name="determining-whether-document-data-is-already-open"></a>确定是否文档数据是已打开  
 在集成的开发环境 (IDE) 中运行文档表 (RDT) 可帮助跟踪是否文档的数据已处于打开状态，如下面的关系图中所示。  
  
 ![DocDataView 图](../extensibility/media/docdataview.gif "Docdataview")  
多视图  
  
 默认情况下，每个视图 （文档视图对象） 包含在其自己的窗口框架中 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>)。 已特别说明，但是，文档数据可以显示多个视图中。 若要启用此功能，Visual Studio，请检查 RDT 以确定问题的文档是否已在编辑器中打开。 当 IDE 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>若要创建编辑器中，在中非 NULL 值返回`punkDocDataExisting`参数指示该文档已在另一个编辑器中打开。 详细了解如何 RDT 函数中，请参阅[运行 Document 表](../extensibility/internals/running-document-table.md)。  
  
 在你<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>实现中，检查文档数据对象中返回`punkDocDataExisting`来确定文档数据是否适合于你的编辑器。 （例如，仅 HTML 数据应显示的 HTML 编辑器。）如果适当，编辑器工厂应为数据提供第二个视图。 如果`punkDocDataExisting`参数不是`NULL`，这可能可能是文档数据对象是在另一个编辑器中打开，或可在更有可能，已存在具有相同编辑器中的不同视图中打开文档数据。 如果在你的编辑器工厂不支持的其他编辑器中打开的文档数据，Visual Studio 将无法打开编辑器工厂。 有关详细信息，请参阅[如何： 附加到文档数据的视图](../extensibility/how-to-attach-views-to-document-data.md)。