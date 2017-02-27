---
title: "IntelliSense 承载 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的智能感知承载"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IntelliSense 承载
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 启用 IntelliSense 承载。  IntellSense 承载可以为不受 Visual Studio 文本编辑器承载代码提供 IntelliSense。  
  
## 承载用法的 IntelliSense  
 在 Visual Studio 中，可以访问完成的所有代码和文本缓冲区可以从任何位置用户界面的 IntelliSense 窗口 \(UI\)。  此的一些示例方案是完成 **监视** 窗口或 " 断点 " 属性 " 窗口定位字段。  
  
### 实现接口  
  
#### IVsIntellisenseHost  
 承载 IntelliSense 弹出窗口的任何 UI 元素必须支持 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口。  默认核心编辑器文本视图包含一次股票 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口实现保留当前的 IntelliSense 功能。  大多数情况下， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口的方法来表示的子集在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 接口实现。  该子集包括 IntelliSense UI 处理，插入符号并选择处理和简单文本替换功能。  此外， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口允许单独的 IntelliSense “主题”和 “context”，以便 IntelliSense 可用于不直接存在于文本缓冲区有关上下文使用的主题提供。  
  
#### IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口提供程序必须执行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> 方法使客户端能够确定哪种类型的 IntelliSense 在宿主功能支持。  
  
 宿主标志，定义在 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)，在摘要。  
  
|IntelliSense 宿主标志|说明|  
|-----------------------|--------|  
|IHF\_READONLYCONTEXT|设置此标志意味着上下文缓冲区只读，并编辑在主题文本中仅发生。|  
|IHF\_NOSEPERATESUBJECT|设置此标志意味着没有单独的 IntelliSense 主题。  此主题存在于上下文缓冲区，例如在传统 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense 系统。|  
|IHF\_SINGLELINESUBJECT|设置此标志。 **监视** 窗口意味着该主题没有多行能够的，例如单个行编辑。|  
|IHF\_FORCECOMMITTOCONTEXT|如果此标志设置，并且上下文缓冲区必须更新，宿主使上下文缓冲区的只读标志会忽略并编辑执行。|  
|IHF\_OVERTYPE|edit \(在主题或上下文\) 在重打模式应完成。|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit 和 IVsIntellisenseHost.AfterCompletorCommit  
 这些回调方法由完成窗口调用，文本提交之前，启用预处理和程序集。  
  
#### IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> 接口是集成开发环境 \(ide\) 使用标准完成窗口的公共的可创建版本 \(IDE\)。  通过使用此 completor 接口，所有 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 接口可以快速实现 IntelliSense。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop>