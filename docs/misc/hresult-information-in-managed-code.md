---
title: "在托管代码的 HRESULT 信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HRESULT, 托管 Vspackage"
  - "Vspackage, HRESULT 信息"
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# 在托管代码的 HRESULT 信息
当遇到 HRESULT 返回值时，托管代码和 COM 之间的交互可能会导致一些问题。  
  
 在 COM 接口中，HRESULT 返回值可以发挥以下作用：  
  
-   提供错误信息（例如 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>）。  
  
-   提供有关正常程序行为的状态信息。  
  
 当 COM 调入托管代码时，HRESULT 可能会导致以下问题：  
  
-   返回小于零的 HRESULT 值（故障代码）的 COM 函数会生成异常。  
  
-   无法辨别定期返回两个或更多个不同成功代码（例如，<xref:Microsoft.VisualStudio.VSConstants.S_OK> 或 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>）的 COM 方法。  
  
 由于许多 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] COM 函数返回小于零的 HRESULT 值或返回不同的成功代码，因此，编写了 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 互操作程序集以便保留方法签名。 所有 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 互操作方法均为 `int` 类型。 HRESULT 值通过互操作层传递，无需更改且不会生成异常。  
  
 由于 COM 函数向调用它的托管方法返回 HRESULT，因此，进行调用的方法必须检查 HRESULT，并根据需要引发异常。  
  
## 处理从 COM 返回到托管代码的 HRESULT  
 当从托管代码调用 COM 接口时，请检查 HRESULT 值并根据需要引发异常。<xref:Microsoft.VisualStudio.ErrorHandler> 类包含 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法，该方法根据传递给它的 HRESULT 值引发 COM 异常。  
  
 默认情况下，每次向 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 传递值小于零的 HRESULT 时，它都会引发异常。 如果此类 HRESULT 是可接受的值，不应引发异常，那么，应在测试完其他 HRESULT 的值后，将这些值传递给 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果所测试的 HRESULT 与显式传递到 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值匹配，则不会引发异常。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> 类包含通用 HRESULT（例如 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 和 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>）和 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] HRESULT（例如 <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 和 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>）的常量。<xref:Microsoft.VisualStudio.VSConstants> 还提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，分别对应于 COM 中的 SUCCEEDED 宏和 FAILED 宏。  
  
 例如，在以下函数调用中，<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> 是可接受的返回值，而其他所有小于零的 HRESULT 均表示错误。  
  
 [!code-vb[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_1.vb)]
 [!code-cs[VSSDKHRESULTInformation#1](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_1.cs)]  
  
 如果有多个可接受的返回值，只需在调用 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 时将其他 HRESULT 值追加到列表中。  
  
 [!code-vb[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/VisualBasic/hresult-information-in-managed-code_2.vb)]
 [!code-cs[VSSDKHRESULTInformation#2](../extensibility/internals/codesnippet/CSharp/hresult-information-in-managed-code_2.cs)]  
  
## 从托管代码将 HRESULT 返回到 COM  
 如果没有发生异常，托管代码会向调用它的 COM 函数返回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。 COM 互操作支持托管代码中强类型化的常见异常。 例如，收到不可接受的 `null` 参数的方法会引发 <xref:System.ArgumentNullException>。  
  
 如果不确定要引发哪个异常，但知道要返回到 COM 的 HRESULT，则可以使用 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 方法引发相应的异常。 即使是非标准错误（例如 <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>），也同样可行。<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 会尝试将传递给它的 HRESULT 映射到强类型化的异常。 如果无法映射，它会改为引发一般的 COM 异常。 最终结果是，从托管代码传递到 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 的 HRESULT 返回到调用它的 COM 函数中。  
  
> [!NOTE]
>  异常会降低性能，它用于指示程序的异常状况。 对于所发生的状况，通常应以内联方式处理，而不是引发异常。  
  
## 请参阅  
 [托管的 VSPackage](../misc/managed-vspackages.md)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [如何：映射 HRESULT 和异常](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)   
 [为交互操作生成 COM 组件](http://msdn.microsoft.com/zh-cn/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [托管的 VSPackage](../misc/managed-vspackages.md)