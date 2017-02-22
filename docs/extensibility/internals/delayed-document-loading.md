---
title: "延迟加载文档 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 延迟加载文档
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当用户重新打开 Visual Studio 解决方案时，不会立即加载的大多数相关联的文档。 处于挂起的初始化状态，则创建该文档窗口框架和占位符文档 \(称为存根 \(stub\) 帧\) 被放在运行文档表 \(RDT\)。  
  
 您的扩展插件可能会导致不必要地加载的查询的文档中的元素，在加载之前的项目文档。 对 Visual Studio，这样可以提高总体内存占用量。  
  
## 文档加载  
 在用户访问该文档，例如通过选择窗口框架的选项卡时，完全初始化的存根 \(stub\) 框架和文档。 也可通过一种扩展，请求该文档的数据，可以通过访问 RDT 直接以获取文档数据，或通过进行以下调用的其中一个间接访问 RDT 来初始化该文档:  
  
-   窗口框架显示方法: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
-   窗口框架 GetProperty 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 对任何下列属性:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 如果您的扩展插件使用托管的代码时，不应调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 除非您确信文档未处于挂起的初始化状态，或者你想要完全初始化的文档... 这是因为此方法始终返回文档数据对象，如有必要创建它。 相反，您应调用的方法之一在 IVsRunningDocumentTable4 接口上。  
  
 如果您的扩展插件使用 c \+ \+，您可以将传递 `null` 不希望的参数。  
  
 通过调用以下方法之一之前要求提供相关的属性，可以避免不必要的文档加载: 寻求其他属性之前。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>。 此方法返回 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 包含的值对象 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 文档尚未初始化的情况。  
  
 通过订阅到一个文档完全在初始化时引发的 RDT 事件已加载了一个文档时，可以找出。 有两种可能:  
  
-   如果事件接收器会实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, ，您可以订阅 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,，  
  
-   否则，您可以订阅 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。  
  
 下面是一个假设文档访问方案。 Visual Studio 中扩展想要显示有关打开的文档的一些信息，例如编辑锁定计数和有关文档数据的某种东西。 枚举中的文档以 RDT 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ，然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 对于每个文档以便检索编辑锁计数和文档数据。 如果文档是处于挂起的初始化状态，则请求文档数据将会使其不必要地初始化。  
  
 这是为了使用做的事情更高效的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 获取编辑锁计数，然后使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 来确定文档是否已初始化。 如果不包括标志 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, ，文档已初始化，并请求与文档数据 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 不会导致任何不必要的初始化。 如果包括标志 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, ，该扩展应避免初始化文档后，才请求文档数据。 这可以 OnAfterAttributeChange\(Ex\) 事件处理程序中检测到。  
  
## 测试以查看它们是否强制执行初始化的扩展  
 没有任何可见线索来指示是否已初始化文档，因此很难找到您的扩展插件强制初始化。 您可以设置轻松验证注册表项，因为它会导致未完全初始化则文字的每个文档的标题 `[Stub]` 标题中。  
  
 在 **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, ，请设置 **StubTabTitleFormatString** 到 **{0} \[存根\]**。