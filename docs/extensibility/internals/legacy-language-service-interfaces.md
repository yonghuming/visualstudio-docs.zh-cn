---
title: "遗留语言服务接口 | Microsoft Docs"
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
  - "IVsLanguageInfo 接口"
  - "语言服务对象"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 遗留语言服务接口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

到任何特定编程语言，一次只能具有语言服务的一个实例。  但是，单个语言服务可以对多个编辑器服务。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不关联语言服务与任何特定的编辑器。  因此，那么，当您请求语言服务操作时，必须确定适当的编辑器中作为参数。  
  
## 公共接口与语言服务  
 编辑器通过调用适当的 VSPackage 中 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 获取语言服务。  中 \(SID\) 传递的服务调用标识符标识请求的语言服务。  
  
 可以实现任意数量的单独的类的核心语言服务接口。  但是，公共方法是实现在单个类的以下接口:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>（可选）  
  
 在所有语言服务必须实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 接口。  它提供有关语言服务的信息，如该语言的本地化名称，文件扩展名与语言服务，以及如何检索 colorizer。  
  
## 其他语言服务接口  
 其他接口可随语言服务。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 请求这些接口实例文本缓冲区的每个实例。  因此，应单独实现这些接口对象中的每一。  下表显示了每个文本缓冲区实例一个实例的接口。  
  
|接口|说明|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|托管代码窗口修饰，如将下拉栏。  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 方法，您可以获取此接口。  对于每个代码窗口。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorizes 语言关键字和分隔符。  使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法，您可以获取此接口。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 调用在绘制时。  避免在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 内的计算密集型工作或性能可能会陷入。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 参数工具提示。  当语言服务标识时指示的字符应显示方法的数据，例如一个左括号，它调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 方法通知文本视图语言服务准备好显示参数信息工具提示。  文本视图然后调用回语言服务使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 接口的方法来获取显示工具提示的所需信息。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 语句完成。  当语言服务准备显示完成列表时，它对文本视图的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。  通过在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 对象的方法，文本视图然后调用回语言服务。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|使用命令处理程序，使文本视图的修改。  您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 实现接口的类还必须实现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 接口。  文本视图通过查询传递给 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 对象检索 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 对象。  应为每个视图中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 对象。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|截获命令该用户类型到代码窗口。  监视从 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 实现的输出提供自定义完成信息和视图修改<br /><br /> 若要传递给文本视图的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 对象，请调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|  
  
## 请参阅  
 [开发语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [清单︰ 创建传统语言服务](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)