---
title: "错误处理和返回值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>错误处理和返回值
Vspackage 和 COM 错误使用相同的体系结构。 `SetErrorInfo`和`GetErrorInfo`函数是 Win32 应用程序编程接口 (API) 的一部分。 在集成的开发环境 (IDE) 中的任何 VSPackage 可以调用这些全局 Win32 Api 来记录丰富的错误消息在接收错误通知时。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供互操作程序集来管理错误的信息。  
  
## <a name="interop-methods"></a>互操作方法  
 为方便起见，IDE 提供了一种方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>，若要使用而不是调用 Win32 Api。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 在托管代码中使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 出错时`HRESULT`到达应在其中显示错误消息的级别 (这通常是该对象实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令处理程序)，IDE 将使用另一种方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，以便显示相应的消息框。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 在托管的代码使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 VSPackage 实施者，作为 COM 对象通常实现`ISupportErrorInfo`。 `ISupportErrorInfo`接口可确保调用链中向上垂直移动可以丰富的错误消息。 跨进程或线程间可能使用的对象都必须支持`ISupportErrorInfo`以确保丰富的错误消息返回给调用方正确封送。  
  
 所有对象，与 VSPackages 迁移有关的并可参与扩展 IDE 中，其中包括编辑器工厂、 编辑器、 层次结构，并提供服务，应都支持丰富的错误消息。 虽然 IDE 不需要这些 VSPackage 对象来实现`ISupportErrorInfo`，始终建议。  
  
 IDE 负责报告错误的信息并显示给用户的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每当`HRESULT`传播到 IDE。 IDE 也是用于创建机制`ErrorInfo`对象。  
  
## <a name="general-guidelines"></a>通用准则  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法以设置和报告是您的 VSPackage 实现的内部错误。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 但是，作为一般规则，请遵循以下准则来处理你的 VSPackage 中的错误消息︰  
  
-   实现`ISupportErrorInfo`VSPackage COM 对象中。  
  
-   创建一种错误报告调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>对象中的方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>的机制  
  
-   让 IDE 通过向用户显示错误<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>在 IDE 中的错误信息  
 以下规则指示如何处理中的错误信息[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE:  
  
-   若要确保陈旧错误信息不报告给用户，防御策略功能该调用一样<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法应先调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 传入`null`清除缓存的错误消息，然后调用任何操作，可能会设置新的错误信息。  
  
-   仅允许使用不直接报告错误消息的函数调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法如果他们要返回的错误`HRESULT`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 允许清除`ErrorInfo`条目指向函数或返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。</xref:Microsoft.VisualStudio.VSConstants.S_OK> 此规则的唯一例外是当调用返回错误`HRESULT`从其接收方可以显式恢复或放心地忽略。  
  
-   任意一方都显式忽略错误`HRESULT`必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>具有<xref:Microsoft.VisualStudio.VSConstants.S_OK>。</xref:Microsoft.VisualStudio.VSConstants.S_OK>方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 否则为`ErrorInfo`另一方将生成错误，而无需提供其自己时，对象可能会意外地使用`ErrorInfo`。  
  
-   生成错误的所有方法`HRESULT`鼓励调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法以提供丰富的错误消息。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 如果返回`HRESULT`是一个特殊`FACILITY_ITF`错误，则说明该方法需要提供适当的`ErrorInfo`对象。 如果返回的错误是标准的系统错误 (例如， <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>， <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>， <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>， <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>，等等) 是可以接受无需显式调用返回的错误代码的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> 当发出一个错误时的防御性编码战略`HRESULT`（包括系统错误），始终调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法中，使用`ErrorInfo`描述更详细地故障或`null`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   返回错误是由另一个调用始发，必须通过取决于收到了来自失败的信息的所有函数都调用中`HRESULT`而无需修改`ErrorInfo`对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo （组件自动化）](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 接口](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
