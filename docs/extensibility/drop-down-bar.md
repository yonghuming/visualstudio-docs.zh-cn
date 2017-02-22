---
title: "下拉栏 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，旧的下拉栏"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 下拉栏
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该下拉栏提供在代码窗口之上包含两个下拉列表。  
  
## 下拉栏接口  
 如下图所示，在 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]，例如，该下拉栏包含用于 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 项目和 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 项目成员函数，。  
  
 ![下拉栏](../extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
下拉栏  
  
 当实现一个下拉栏时，有四个主要接口重要:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     实现此接口插入该下拉栏的内容。  每个下拉组合包含纯文本或花梢文本 \(粗体，下划线或斜体\)，对于 windows 文本的字体着色或灰显的字体着色，并且可以在该下拉项旁边还可以提供一个小的位图。  类似于 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 接口，位图图像在图像的列表。  每个下拉组合可能具有不同的图像列表;但是，每个图像列表中必须包含同一高度的图像。  此外，使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> 方法，即，可以为每个组合提供工具提示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     调用此接口来创建或销毁代码窗口的下拉栏。  此接口还可用于确定一个下拉栏是否已附加到代码窗口通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 方法。  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 的 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 从 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     调用此接口直接与该下拉栏通信。  在某个可以使用此接口强制下拉栏内容的刷新或更改选择列表框中。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果注册了语言服务注册表项的 `ShowDropdownBarOption` ，则代码窗口管理器必须监视此事件与用户首选项同步有关是否应显示该下拉栏。  如果没有注册在语言服务键的此选项，则显示或隐藏该下拉栏的选项禁用在 **选项** 菜单。  
  
## 附加一个下拉栏到代码窗口  
 若要附加一个下拉栏到代码窗口，则在创建集合时，语言服务应附加到该下拉栏，当 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 调用方法时。  如果对 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> 方法的调用指示一个下拉栏尚不存在，则调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>。  访问，当 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 实现附加属性， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> 接口，调用从 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 指针的 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 返回给您。  
  
## 请参阅  
 [通过使用旧 API 的自定义代码窗口](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [对旧语言服务中的导航栏的支持](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)