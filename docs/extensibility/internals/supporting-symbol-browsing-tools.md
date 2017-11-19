---
title: "支持符号浏览工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b9e9963b43e6ca2049337fdfdf76b0a1314ae32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-symbol-browsing-tools"></a>支持符号浏览工具
**对象浏览器**，**类视图**，**调用浏览器**和**查找符号结果**工具提供了一些符号浏览 Visual Studio 中的功能。 这些工具显示的符号的分层树视图，并显示在树中的符号之间的关系。 符号可能代表命名空间、 对象、 类、 类成员和各种组件中包含其他语言元素。 这些组件包括 Visual Studio 项目中，外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]组件和类型 (.tlb) 库。 有关详细信息，请参阅[查看代码的结构](../../ide/viewing-the-structure-of-code.md)。  
  
## <a name="symbol-browsing-libraries"></a>符号浏览库  
 为语言实施者，你可以扩展 Visual Studio 符号浏览功能，通过创建跟踪在组件中的符号，并通过一组接口的 Visual Studio 对象管理器提供的符号列表的库。 描述一个库<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>接口。 Visual Studio 对象管理器响应新数据的请求来自符号浏览工具通过从库中获取数据和组织它。 随后将填充，或使用所请求的数据更新工具。 若要获取 Visual Studio 对象管理器中，指<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，传递<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>服务 ID 到`GetService`方法。  
  
 每个库必须注册 Visual Studio 对象管理器，在所有库收集的信息。 若要注册库，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 具体取决于哪一种工具启动请求，Visual Studio 对象管理器查找合适的库，并请求数据。 数据传输之间的库和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所描述的符号列表中的对象管理器<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>接口。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对象管理器负责定期刷新符号浏览工具，以反映在库中包含的最新数据。  
  
 下图包含请求/数据交换过程之间的库和 Visual Studio 对象管理器中的主要元素的示例。 在关系图中的接口为托管的代码应用程序的一部分。  
  
 ![库和对象管理器之间的数据流](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 若要向 Visual Studio 对象管理器提供的符号的列表，你必须先注册库的 Visual Studio 对象管理器通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 注册了库后，Visual Studio 对象管理器将请求的功能的库的某些信息。 例如，请求的库标志，并通过调用支持类别<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>方法。 在某些时候，当工具之一进行请求数据通过此库对象管理器请求顶级的符号列表通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>方法。 在响应中，库生成的符号列表，并将它暴露给通过 Visual Studio 对象管理器<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>接口。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对象管理器确定多少项是在列表中，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>方法。 以下的所有请求与给定项列表中，并提供每个请求中的项索引号。 Visual Studio 对象管理器会将收集的信息的类型、 可访问性，以及其他属性的项通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>方法。  
  
 它通过调用中确定的项名称<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>方法，并通过调用请求图标信息<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法。 该图标的项名称的左侧显示，并描述了该项目、 可访问性，以及其他属性的类型。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]对象管理器调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>方法来确定给定的列表项是否可展开，并具有子项。 对象管理器 UI 发送请求以展开元素，如果通过调用请求符号的子列表<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>方法。 此过程将继续与正在按需生成树的不同部分。  
  
> [!NOTE]
>  若要实现本机代码的符号提供程序，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>接口。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 注册与对象管理器的库](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何： 公开的库提供给对象管理器中的符号列表](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [如何：识别库中的符号](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)