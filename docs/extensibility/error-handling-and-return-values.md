---
title: "错误处理和返回值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a197bb5dd12c1d8404ddf63976f9dbf4b63823
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-handling-and-return-values"></a>错误处理和返回值
Vspackage 和 COM 错误使用相同的体系结构。 `SetErrorInfo`和`GetErrorInfo`函数是 Win32 应用程序编程接口 (API) 的一部分。 在集成的开发环境 (IDE) 中的任何 VSPackage 可以调用这些到记录丰富的错误信息的全局 Win32 Api 接收的错误通知时。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供互操作程序集来管理错误的信息。  
  
## <a name="interop-methods"></a>互操作方法  
 为方便起见，IDE 提供了一种方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>，则应使用而不是调用 Win32 Api。 在托管的代码使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>。 出错时`HRESULT`到达应在其中显示错误消息的级别 (这通常是该对象实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令处理程序)，IDE 使用另一种方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，以显示相应的消息框。 在托管的代码使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
 为 VSPackage 实施者，COM 对象通常实现`ISupportErrorInfo`。 `ISupportErrorInfo`接口可确保调用链可以垂直移丰富的错误信息。 跨进程或跨线程可能使用的对象必须支持`ISupportErrorInfo`以确保丰富的错误信息返回到调用方正确封送。  
  
 所有对象，将与 Vspackage 和可参与扩展 IDE，包括编辑器工厂、 编辑器、 层次结构，并提供服务，应都支持丰富的错误信息。 尽管 IDE 不要求这些 VSPackage 对象以实现`ISupportErrorInfo`，它始终建议。  
  
 IDE 负责报告错误信息并显示给用户的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每当`HRESULT`传播到 IDE。 IDE 也是用于创建机制`ErrorInfo`对象。  
  
## <a name="general-guidelines"></a>通用准则  
 你可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>设置和报告错误的你的 VSPackage 实现内部的方法。 但是，作为一般规则，请遵循以下准则来处理你的 VSPackage 中的错误消息：  
  
-   实现`ISupportErrorInfo`VSPackage COM 对象中。  
  
-   创建错误报告调用的机制<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>中实现的对象的方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
-   允许通过向用户显示错误 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。  
  
## <a name="error-information-in-the-ide"></a>在 IDE 中的错误信息  
 以下规则指示如何处理中的错误信息[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE:  
  
-   与防御性策略，若要确保陈旧错误信息不报告给用户，该调用的函数<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法应首先调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 传入`null`清除缓存的错误消息，然后调用任何内容，可能会设置新的错误信息。  
  
-   仅允许直接不报告错误消息的函数调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法如果它们返回错误`HRESULT`。 允许以清除`ErrorInfo`函数或返回的条目<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 此规则的唯一例外是当调用返回错误`HRESULT`从接收方可以显式恢复或放心地忽略。  
  
-   任何显式忽略错误一方`HRESULT`必须调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法替换<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 否则为`ErrorInfo`而无需提供其自己的另一方生成一个错误时，对象可能会意外地使用`ErrorInfo`。  
  
-   生成错误的所有方法`HRESULT`建议调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法以提供丰富的错误信息。 如果返回`HRESULT`是一个特殊`FACILITY_ITF`错误，则该方法需要提供合适`ErrorInfo`对象。 如果返回的错误是标准的系统错误 (例如， <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>， <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>， <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>， <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>，等等。) 是可接受不通过显式调用返回错误代码的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。 作为时发出错误防御性编码策略`HRESULT`（包括系统错误），始终调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，使用`ErrorInfo`描述中更详细的失败位置或`null`。  
  
-   返回错误的另一调用产生必须通过从失败中接收到的信息的所有函数都调用中`HRESULT`而无需修改`ErrorInfo`对象。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo （组件自动化）](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 接口](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)