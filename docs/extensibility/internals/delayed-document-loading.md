---
title: "延迟文档加载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 794eccaf59b65044840d459bbde2e17eab8684a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="delayed-document-loading"></a>延迟文档加载
当用户重新打开 Visual Studio 解决方案时，不会立即加载大部分关联的文档。 文档窗口框架将创建处于挂起的初始化状态，并占位符文档 （称为存根 （stub） 帧） 被放在正在运行文档表 (RDT)。  
  
 你的扩展可能会导致通过查询在文档中的元素，在加载前不必要地加载项目文档。 这样可以提高总体内存占用量 for Visual Studio。  
  
## <a name="document-loading"></a>文档加载  
 当用户访问该文档，例如通过选择窗口框架的选项卡时，完全初始化的存根 （stub） 框架和文档。 也可通过扩展，请求该文档的数据，通过访问 RDT 直接以获取文档的数据，或通过进行以下调用之一间接访问 RDT 初始化文档：  
  
-   窗口框架显示方法： <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
-   窗口框架 GetProperty 方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>上任何以下属性：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 如果你的扩展使用托管的代码时，不应调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>除非您确信文档未处于挂起的初始化状态，或者你想要完全初始化后的文档... 这是因为此方法始终返回文档数据对象，如有必要创建它。 相反，您应调用的方法之一 IVsRunningDocumentTable4 接口上。  
  
 如果你的扩展使用 c + +，你可以传递`null`你不希望的参数。  
  
 你可以通过之前你请求的相关属性调用以下方法之一来避免不必要的文档加载： 寻求其他属性之前。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>。 此方法返回<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>包括一个值的对象<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>如果文档尚未初始化。  
  
 通过订阅到完全初始化文档时引发的 RDT 事件已加载文档时，可以找出。 有两种可能：  
  
-   如果事件接收器实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>，您可以订阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>，  
  
-   否则，你可以订阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。  
  
 下面是假设的文档访问方案。 Visual Studio 中扩展想要显示有关打开的文档的一些信息，例如编辑锁定计数和有关文档数据的某种东西。 它枚举 RDT 使用中的文档<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>，然后调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>以检索编辑锁计数和文档数据的每个文档。 如果文档处于挂起的初始化状态，则请求文档数据将会导致它不必要地初始化。  
  
 这是用于执行此操作的更高效方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>以使编辑锁计数，然后使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>来确定文档是否已初始化。 如果不包括标志<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，文档已初始化，并请求使用的文档数据<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>不会导致任何不必要的初始化。 如果标志中确实包含<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，该扩展应避免在初始化文档之前请求的文档数据。 这可以在 OnAfterAttributeChange(Ex) 事件处理程序检测到。  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>测试扩展，以查看它们是否强制初始化  
 没有可见的提示，以指示是否已初始化文档，因此它可能很难了解你的扩展强制初始化。 你可以设置轻松验证注册表项，因为它会导致未完全初始化则文字每个文档的标题`[Stub]`标题中。  
  
 在**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**，将其设置**StubTabTitleFormatString**到**{0} [存根]**。