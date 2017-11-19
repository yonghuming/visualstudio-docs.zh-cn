---
title: "下拉栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f5da476bb9b54b536cb296112d578574822e410
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="drop-down-bar"></a>下拉栏
下拉栏提供在代码窗口顶部，包含两个下拉列表。  
  
## <a name="drop-down-bar-interfaces"></a>下拉栏接口  
 在[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，例如，下拉栏包含列表[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]项和[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]项成员函数，如下图中所示。  
  
 ![拖放 &#45; 向下条](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
下拉栏  
  
 当实现一个下拉栏，有四个接口最为重要的：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     实现此接口可插入下拉条的内容。 每个下拉组合可以包含纯文本或特别文本 (粗体、 下划线、 或斜体)、 可以为窗口文本字体着色或处于灰显状态的字体着色，和可以根据需要提供一个下拉列表项旁边的小位图。 类似于<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>接口，将位图图像提供图像列表中。 每个下拉组合都可以具有不同的图像列表;但是，每个图像列表必须包含图像的高度相同。 此外，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>方法，你可以为每个组合提供工具提示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     调用此接口可创建或销毁代码窗口的下拉栏。 此外可以使用此接口来确定是否下拉栏已附加到代码窗口通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法。 调用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>为<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     调用此接口可直接与下拉栏进行通信。 你可以使用此接口的下拉列表进行强制刷新栏内容或更改其中一个列表框中的选择。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果你注册`ShowDropdownBarOption`在您语言服务的注册表项，然后你的代码窗口管理器必须监视此事件与有关是否应显示的下拉栏的用户首选项进行同步。 如果不在你语言的服务密钥，注册此选项，则在禁用的选项显示或隐藏下拉栏**选项**菜单。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>附加到代码窗口的下拉栏  
 若要附加下拉栏到代码窗口中，创建时，语言服务应该附加到下拉栏时<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>调用方法。 如果调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法指示下拉栏不已不存在，然后调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>。 访问<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>界面，请调用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>指针返回到你时你<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>实现已附加。  
  
## <a name="see-also"></a>另请参阅  
 [通过使用旧版 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [旧版语言服务中的导航栏支持](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)