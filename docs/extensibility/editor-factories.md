---
title: "编辑器工厂 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bfef7e641bc8f7e041242ce28110845855c2a65
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="editor-factories"></a>编辑器工厂
编辑器工厂创建编辑器对象，并将它们放在窗口框架，称为物理视图中。 它创建的文档数据和所需创建编辑器和设计器的文档视图对象。 创建 Visual Studio 核心编辑器和任何标准编辑器需要编辑器工厂。 也可以使用的编辑器工厂创建的自定义编辑器。  
  
 通过实现创建编辑器工厂<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口。 下面的示例演示如何实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>创建编辑器工厂：  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 编辑器是加载首次打开该编辑器所处理的文件类型。 你可以选择特定的编辑器或默认编辑器打开。 如果你选择的默认编辑器，集成的开发环境 (IDE) 将确定正确编辑器打开，然后打开它。 有关详细信息，请参阅[确定哪种编辑器在项目中打开文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## <a name="registering-editor-factories"></a>注册编辑器工厂  
 你可以使用一个编辑器，你已创建之前，您首先必须注册信息，包括它可以处理的文件扩展名。  
  
 如果你的 VSPackage 在托管代码中编写的你可以使用托管包框架 (MPF) 方法<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>若要注册的编辑器工厂之后加载你的 VSPackage。 如果你的 VSPackage 编写在非托管代码中，则必须使用注册你的编辑器工厂<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>服务。  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>通过使用注册编辑器工厂托管代码  
 您必须在你的 VSPackage 的注册你的编辑器工厂`Initialize`方法。 首先调用`base.Initialize`，然后调用<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>每个编辑器工厂  
  
 在托管代码中，是要注销的编辑器工厂，无需过程，因为 VSPackage 将为你处理此。 此外，如果你的编辑器工厂实现<xref:System.IDisposable>，注销时自动释放。  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>通过使用非托管的代码中注册的编辑器工厂  
 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>实现你的编辑器包，使用`QueryService`方法来调用`SVsRegisterEditors`。 执行此操作返回一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>。 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法，从而将的实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>接口。 你必须 mplement<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>在单独的类。  
  
## <a name="the-editor-factory-registration-process"></a>编辑器工厂注册过程  
 Visual Studio 加载使用编辑器工厂编辑器时，将发生以下过程：  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目系统调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  此方法返回编辑器工厂。 Visual Studio 延迟加载编辑器的包，但是，直到项目系统实际上需要编辑器。  
  
3.  当项目系统需要编辑器时，Visual Studio 会调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>，返回的文档视图和文档数据对象的专用化的方法。  
  
4.  如果调用由 Visual Studio 编辑器工厂使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>返回文档数据对象和文档视图对象、 Visual Studio 然后创建文档窗口，将文档视图对象放在它，而使到正在运行文档中的条目表 (RDT) 的文档数据对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [运行文档表](../extensibility/internals/running-document-table.md)