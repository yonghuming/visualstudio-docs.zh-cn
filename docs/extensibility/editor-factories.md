---
title: "编辑器工厂 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，旧的编辑器工厂"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 编辑器工厂
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

编辑工厂。窗架创建编辑对象并将它们放置，也称为的一个物理视图。  它创建文档数据和文档需要创建编辑器和设计器的视图对象。  需要编辑工厂创建 Visual Studio 核心编辑器和所有标准编辑。  自定义编辑器可以通过编辑工厂选择性地创建。  
  
 通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 接口创建一个编辑工厂。  下面的示例演示如何实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 创建编辑工厂:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 您打开该编辑器处理的文件类型编辑器第一次加载。  可以选择打开一特定编辑器或默认编辑器。  如果选择默认编辑器，集成开发环境 \(IDE\) \(ide\) 确定正确的编辑器中打开然后将其打开。  有关更多信息，请参见 [确定哪个编辑器随即打开，在项目中的文件](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)。  
  
## 注册表编辑器工厂  
 在将您创建的编辑之前，必须先有关它可以处理的方式注册信息，包括文件扩展名。  
  
 如果 VSPackage 用托管代码编写，可以使用托管包 framework \(MPF\) 方法 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 注册编辑器工厂，在 VSPackage 加载之后。  如果 VSPackage 在非托管代码编写的，使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> 服务，则必须注册编辑器工厂。  
  
### 注册使用托管代码的一个版本工厂  
 必须注册 VSPackage 中 `Initialize` 方法的编辑工厂。  第一次调用 `base.Initialize`，然后调用每个编辑工厂的 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>  
  
 在托管代码中，因为 VSPackage，将会处理您的，不需要注销每编辑工厂。  此外，，如果编辑工厂实现 <xref:System.IDisposable>，它将自动进行配置，以便中注销时。  
  
### 注册使用非托管代码的一个版本工厂  
 在编辑器软件包的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 实现中，使用 `QueryService` 方法调用 `SVsRegisterEditors`。  执行此操作返回指向 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>。  通过将 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 接口的实现调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 方法。  必须在单独的类的 mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 。  
  
## 编辑工厂注册过程  
 使用编辑器工厂，，那么，当 Visual Studio 加载编辑器以下过程发生:  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目系统调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  此方法返回编辑工厂。  ，但是， Visual Studio 延迟加载编辑的包，直到项目系统确实需要编辑器。  
  
3.  当项目系统需要编辑器时， Visual Studio 会调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>，返回文档视图和文档数据对象的专用方法。  
  
4.  如果由 Visual Studio 调入编辑工厂使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 返回文档数据对象并记录视图对象，然后 Visual Studio 在创建文档窗口中，将文档视图对象，并提交项转换为文档文档 \(RDT\)数据对象的表的运行。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [正在运行的 Document 表](../extensibility/internals/running-document-table.md)