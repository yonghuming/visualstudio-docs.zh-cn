---
title: "支持符号浏览工具 | Microsoft Docs"
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
  - "符号，符号浏览工具"
  - "浏览器中，符号浏览器"
  - "符号浏览工具"
  - "库"
  - "IVsLibrary2 接口，符号浏览工具"
  - "IVsSimpleLibrary2 接口，符号浏览工具"
  - "符号浏览工具，库管理器"
  - "symbols"
  - "库、 符号浏览工具"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 支持符号浏览工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**对象浏览器**、 **类视图**、 **调用浏览器** 和 **查找符号结果** 工具提供符号在 Visual Studio 中浏览功能。  这些工具在树中符号分层树视图显示的符号之间的关系。  符号可能表示命名空间、对象、类、类成员以及各种元素包含的其他语言元素。  组件包括 Visual Studio 项目、外部 [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] 元素和类型库 \(.tlb\)。  有关更多信息，请参见 [查看代码的结构](../../ide/viewing-the-structure-of-code.md)。  
  
## 符号浏览库  
 作为语言实现，可以扩展 Visual Studio 符号浏览功能。通过创建跟踪在元素的符号并提供列表符号给 Visual Studio 对象管理器遍历组接口的库。  库由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> 接口所描述的。  Visual Studio 对象管理器响应需要从符号浏览工具的新数据通过从库的数据和组织它。  随后填充或更新具有所请求的数据的工具。  若要获取对 Visual Studio 对象管理器， <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 服务标识符为 `GetService` 方法。  
  
 每个库必须具有 Visual Studio 对象管理器注册，收集所有库的信息。  注册库，调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。  根据哪个工具启动请求， Visual Studio 对象管理器找到相应的库并请求数据。  该数据移到库和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器之间 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 接口所描述的列表符号。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器来定期刷新符号浏览工具反映在库中包含的最新数据。  
  
 数据交换的关系图下面包含请求的关键元素示例\/进程在库和 Visual Studio 对象管理器之间。  在关系图的接口是托管代码应用程序的一部分。  
  
 ![库与对象管理器间的数据流](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 若要提供列表符号给 Visual Studio 对象管理器，可以通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法必须先注册了 Visual Studio 对象管理器的库。  在库注册后， Visual Studio 对象管理器请求有关的库功能的特定信息。  例如，通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> 方法请求库标志和支持的类别。  有时，那么，当某个工具请求从该库中的数据时，对象管理器请求顶部列表符号通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> 方法。  作为响应合理库生成符号列表并将其显示在 Visual Studio 对象管理器通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 接口。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器确定多少项列表中通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 方法。  所有后面的请求与列表中的特定项相关并提供在每个请求的项的索引号。  Visual Studio 对象管理器继续调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 方法收集有关类型、辅助功能和项目的其他属性的信息。  
  
 它通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 方法来确定该项目的名称并通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 方法请求图标信息。  图标在项目名称左侧显示并表示项目、辅助功能以及其他属性的类型。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 方法确定给定点是否列表项可以展开且具有子项。  如果 UI 发送一个请求展开元素，对象管理器请求子列表符号通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 方法。  处理继续生成的树的不同部分中按需下载。  
  
> [!NOTE]
>  若要实现一个本机代码符号提供程序，请使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 接口。  
  
## 请参阅  
 [如何: 注册库与对象管理器](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何: 公开库对对象管理器提供的符号列表](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [如何: 确定库中的符号](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)