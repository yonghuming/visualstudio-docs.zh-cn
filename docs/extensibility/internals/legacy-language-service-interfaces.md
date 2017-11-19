---
title: "旧语言服务接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>旧语言服务接口
对于任何特定的编程语言，会有语言服务的一个实例一次。 但是，单一语言服务可以提供多个编辑器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不是将语言服务与任何特定编辑器相关联。 因此，当你请求的语言服务操作，你必须作为参数来确定适当的编辑器。  
  
## <a name="common-interfaces-associated-with-language-services"></a>与语言服务相关联的公共接口  
 编辑器通过调用获取语言服务<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>上适当的 VSPackage。 在此调用中传递的 ID (SID) 的服务标识所请求的语言服务。  
  
 你可以在任意数量的单独的类上实现核心语言服务接口。 但是，常见方法是在单个类中实现以下接口：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>（可选）  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>必须在所有语言服务上实现接口。 它提供有关你的语言服务，如语言中，与语言服务，以及如何检索着色器关联的文件扩展名的本地化名称的信息。  
  
## <a name="additional-language-service-interfaces"></a>其他语言服务接口  
 可以使用你语言服务提供其他接口。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]请求这些接口的文本缓冲区每个实例的单独实例。 因此，你应实现这些接口的每个在其自己的对象上。 下表显示需要每个文本缓冲区实例的一个实例的接口。  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理代码窗口修饰，如下拉栏。 你可以通过使用来获取此接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。 还有一个<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>每个代码窗口。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|语言关键字和分隔符，会对着色。 你可以通过使用来获取此接口<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>在绘制时调用。 避免在计算密集型工作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>或性能可能会受到影响。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供了 IntelliSense 参数工具提示。 当语言服务识别的字符，该值指示该方法数据应是显示，例如左括号，它将调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法通知文本的视图，该语言服务已准备好显示参数信息工具提示。 文本视图然后返回到语言服务通过使用调用的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>接口来获取所需的信息显示工具提示。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供了 IntelliSense 语句结束。 当语言服务已准备就绪，以显示完成列表时，它将调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>文本视图上的方法。 文本视图然后返回到语言服务通过使用调用方法上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>对象。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|允许进行修改的文本视图使用的命令处理程序。 类实现在其中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>接口还必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口。 文本视图检索<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>对象通过查询<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>对象传递到<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。 应该发出一个<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>对于每个视图的对象。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|截获用户键入到代码窗口的命令。 监视输出你<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>实现，以提供自定义完成信息并查看修改<br /><br /> 若要将传递你<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>对象文本视图，请调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|  
  
## <a name="see-also"></a>另请参阅  
 [开发旧语言服务](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [清单：创建旧版语言服务](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)