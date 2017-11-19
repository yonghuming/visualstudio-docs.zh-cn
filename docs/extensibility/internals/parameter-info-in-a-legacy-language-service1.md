---
title: "参数信息，请参阅旧语言 Service1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f3fd29f46f0edb184b3e0cd5e6ddc766ffc94de
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>参数信息，请参阅旧语言服务
IntelliSense 参数信息工具提示向用户提供有关他们的语言构造中的位置的提示。  
  
 旧语言服务实现的 VSPackage，一部分但实现语言服务功能的新方法是使用 MEF 扩展。 若要了解详细信息，请参阅[扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议你开始使用新的编辑器 API 越早越好。 这将改善语言服务的性能，并让您充分利用新的编辑器功能。  
  
## <a name="how-parameter-info-tooltips-work"></a>参数信息工具提示的工作原理  
 当在编辑器中键入一条语句时，VSPackage 将显示包含键入的语句的定义的小工具提示窗口。 例如，如果键入 Microsoft 基础类 (MFC) 语句 (如`pMainFrame ->UpdateWindow`)，然后按左括号密钥用于开始列出参数，显示的定义，则出现的方法提示`UpdateWindow`方法。  
  
 参数信息工具提示是通常与语句结束结合使用。 它们是最适用于具有参数或其他信息格式化后的方法名称或关键字的语言。  
  
 参数信息工具提示是通过命令截获语言服务启动的。 若要截获用户字符，语言服务对象必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口，并传递指向的指针的文本视图你<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>实现中的，通过调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>中的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口。 命令筛选器截获到代码窗口中键入的命令。 监视知道何时向用户显示参数信息的命令信息。 用于语句完成、 错误标记和等，可以使用相同的命令筛选器。  
  
 当你键入的关键字，该语言服务可以为其提供提示时，然后该语言服务创建<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>对象并调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>中的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>通知 IDE 以显示提示接口。 创建<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>对象使用`VSLocalCreateInstance`并指定组件类`CLSID_VsMethodTipWindow`。 `VsLocalCreateInstance`是调用标头文件 vsdoc.h 中定义的函数`QueryService`为本地注册表和调用`CreateInstance`此对象上`CLSID_VsMethodTipWindow`。  
  
## <a name="providing-a-method-tip"></a>提供的方法提示  
 若要提供的方法提示，请调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>中的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>接口，将其传递的实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>接口。  
  
 当你<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>调用类，其方法调用顺序如下：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     返回当前的文本缓冲区中的位置和相关数据的长度。 这会指示 IDE 以不会掩盖与工具提示窗口该数据。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     返回要最初显示方法数 （从零开始的索引）。 例如，如果返回零，然后第一种重载的方法最初显示。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     返回在当前上下文中适用的重载方法的数目。 如果返回一个值大于 1 的此方法，然后文本视图显示的向上和向下箭头为你。 如果单击向下箭头，IDE 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>方法。 如果单击向上箭头时，IDE 调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     对多个调用过程中构造的参数信息工具提示文本<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     返回要显示在方法中的参数数量。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     如果返回与想要显示的重载相对应的方法数字时，调用此方法，通过调用后接<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     通知你语言服务更新编辑器时显示的方法提示。 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>方法，调用以下命令：  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     接收调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法时关闭方法提示窗口。