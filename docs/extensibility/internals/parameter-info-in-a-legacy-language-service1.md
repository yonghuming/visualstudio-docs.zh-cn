---
title: "传统语言服务中的参数信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "语言服务，方法的提示"
  - "方法的提示"
  - "语言服务，参数信息工具提示"
  - "IVsMethodData 接口"
  - "参数信息 (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 传统语言服务中的参数信息
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

参数的 IntelliSense 信息工具提示为用户提供有关它们处于一种语言构造的提示。  
  
 旧的语言服务实现为作为 VSPackage 的一部分，但实现语言服务功能的较新方法是使用 MEF 扩展。 若要获得详细信息，请参阅 [扩展编辑器和语言服务](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我们建议在开始尽可能快地使用新的编辑器 API。 这将提高您的语言服务的性能，并让您充分利用新的编辑器功能。  
  
## 参数信息工具提示的工作方式  
 当在编辑器中键入一条语句时，VSPackage 显示包含键入的语句的定义的小工具提示窗口中。 例如，如果您键入的 Microsoft 基础类 \(MFC\) 语句 \(如 `pMainFrame ->UpdateWindow`\)，然后按左括号密钥用于开始列出参数，其中显示的定义，则出现的方法提示 `UpdateWindow` 方法。  
  
 参数信息工具提示通常是与语句完成功能结合使用。 它们是最适用于具有参数或其他信息格式化后的方法名称或关键字的语言。  
  
 通过命令拦截该语言服务启动参数信息工具提示。 若要截获用户字符，您的语言服务对象必须实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口，并在文本视图将指针传递至您 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 实现中的，通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 中的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口。 中的命令过滤器截获到代码窗口中键入的命令。 监视命令信息如何确定何时向用户显示参数信息。 对于语句完成、 错误的标记，其含义，可以使用相同的命令筛选器。  
  
 当您键入的关键字的语言服务可以为其提供提示时，然后该语言服务创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 对象并调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 中的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 通知 IDE 以显示提示接口。 创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 对象使用 `VSLocalCreateInstance` 并指定组件类 `CLSID_VsMethodTipWindow`。`VsLocalCreateInstance` 是一个函数中调用的标头文件 vsdoc.h 定义 `QueryService` 本地注册表以及调用 `CreateInstance` 此对象上 `CLSID_VsMethodTipWindow`。  
  
## 提供的方法提示  
 若要提供的方法提示，请调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 中的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 接口，并向其传递的实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 接口。  
  
 当您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 调用类，按以下顺序调用其方法︰  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     返回当前文本缓冲区中的位置和相关数据的长度。 这会指示 IDE 以使该数据与工具提示窗口不清楚。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     返回要最初显示方法数 （从零开始的索引）。 例如，如果返回零，则第一种重载的方法最初呈现。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     返回当前上下文中适用的重载方法的数目。 如果返回一个值大于 1 的此方法，然后在文本视图显示向上和向下箭头为您。 如果您单击向下箭头，IDE 会调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 方法。 如果单击向上箭头时，IDE 会调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     在多次调用过程中构造的参数信息工具提示文本 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     返回要显示在方法中的参数数量。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     如果返回一个与您要显示的重载相对应的方法数字时，调用此方法，然后通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     会通知您的语言服务时将显示的方法提示更新编辑器。 在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 方法，通过调用以下︰  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     接收到呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 方法时关闭方法提示窗口。