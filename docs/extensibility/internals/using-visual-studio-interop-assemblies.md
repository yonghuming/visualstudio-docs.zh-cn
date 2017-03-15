---
title: "使用 Visual Studio 互操作程序集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio 互操作程序集
Visual Studio 互操作程序集使托管应用程序以访问提供 Visual Studio 可扩展性的 COM 接口。 有直接的 COM 接口与它们互操作的版本之间有些区别。 例如，Hresult 通常表示为一个整数值和需要为异常，相同的方式处理和 (尤其是 out 参数） 的参数的处理方式不同。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>处理从 COM 返回到托管代码的 HRESULT  
 当从托管代码调用 COM 接口时，请检查 HRESULT 值并根据需要引发异常。 <xref:Microsoft.VisualStudio.ErrorHandler>类包含的<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>方法，它会引发 COM 异常，具体取决于传递给它的 HRESULT 值</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A></xref:Microsoft.VisualStudio.ErrorHandler>  
  
 默认情况下，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>每当它传递的值小于零的 HRESULT 时引发异常。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 在这种 Hresult 是可接受的值、 何地应引发任何异常的情况下，其他 HRESULT 的值应传递给<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>测试值之后。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 如果所测试的 HRESULT 匹配显式传递到的任何 HRESULT 值<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>，不会引发异常。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>类包含常量用于常见的 HRESULT，例如，<xref:Microsoft.VisualStudio.VSConstants.S_OK>和<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]HRESULT，例如，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>此外提供了<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>和<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>方法，这对应于 COM 中的成功和失败宏</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A></xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 例如，考虑以下函数调用，在其中<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>是可接受的返回值，但其他 HRESULT 小于零表示一个错误。</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 如果有多个可接受的返回值，只是可以将其他 HRESULT 值追加到<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>对的调用中的列表  
  
 [!code-vb[VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>从托管代码将 HRESULT 返回到 COM  
 如果没有发生异常，托管的代码返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>到 COM 函数调用它。</xref:Microsoft.VisualStudio.VSConstants.S_OK> COM 互操作支持托管代码中强类型化的常见异常。 例如，接收不可接受的方法`null`参数将引发<xref:System.ArgumentNullException>。</xref:System.ArgumentNullException>  
  
 如果您不能确定哪个异常引发，但您知道相应的 HRESULT 您想要返回到 COM，您可以使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>方法会引发相应的异常。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 这适用于即使使用了非标准的错误，例如， <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>尝试将映射 HRESULT 传递给它为强类型化的异常。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 如果无法映射，它会改为引发一般的 COM 异常。 最终结果是，HRESULT 将传递给<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>从托管代码中会返回到 COM 函数调用它。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  异常会降低性能，它用于指示程序的异常状况。 对于所发生的状况，通常应以内联方式处理，而不是引发异常。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 参数作为类型 void * * 传递  
 [Out] 已定义为类型的参数查找`void **`com 接口，但被定义为`[``iid_is``]`中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。  
  
 有时，将生成一个 COM 接口`IUnknown`对象和 COM 接口然后将其作为传递类型`void **`。 这些接口是特别重要因为如果该变量被定义为 [out] 在 IDL，则`IUnknown`对象是使用引用计数`AddRef`方法。 如果该对象不能正确处理，则会发生内存泄漏。  
  
> [!NOTE]
>  `IUnknown`对象创建的 COM 接口并在一个 [out] 变量中返回导致出现内存泄漏，如果未显式释放。  
  
 处理此类对象的托管的方法应该将<xref:System.IntPtr>作为指针来`IUnknown`对象，并调用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法来获取该对象。</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> 然后，调用方应转换到适当的任何类型的返回值。 当不再需要该对象时，调用<xref:System.Runtime.InteropServices.Marshal.Release%2A>释放它。</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 下面是一个示例说明如何调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法和处理`IUnknown`正确对象︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  已知下列方法将传递`IUnknown`作为类型<xref:System.IntPtr>。</xref:System.IntPtr>对象的指针 本部分中所述，则处理它们。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out 一个] 可选参数  
 查找定义作为 [out] 参数的数据类型 (`int`， `object`，依此类推) 在 COM 接口，但被定义为在相同的数据类型的数组[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。  
  
 有些 COM 接口，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，将 [out] 参数为可选。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> 如果对象不是必需的这些 COM 接口返回`null`指针作为该参数而不是创建 [out] 对象的值。 这是设计使然。 对于这些接口，`null`指针被假定为 VSPackage，正确行为的一部分，且不会返回错误。  
  
 因为 CLR 不允许为一个 [out] 参数的值`null`，这些接口的设计行为的部件不是托管代码中直接使用。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受影响的接口的互操作程序集方法要解决此问题，通过将相关参数定义为数组，因为 CLR 允许将传递`null`数组。  
  
 这些方法中的托管的实现应放置`null`到参数时没有任何要返回的数组。 否则为创建正确类型的单一元素数组并放置在数组中返回的值。  
  
 托管的可选 [out] 一个接口从其中接收信息的方法参数将参数接收为数组。 只需查看该数组的第一个元素的值。 如果不是`null`，它是原始参数一样处理的第一个元素。  
  
## <a name="passing-constants-in-pointer-parameters"></a>指针参数中传递常量  
 查找的参数定义为 [in] COM 接口中的指针，但定义为<xref:System.IntPtr>键入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。</xref:System.IntPtr>  
  
 COM 接口传递特殊值，例如 0、-1 或 – 2，而不是一个对象指针时，会出现类似问题。 与不同[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]，CLR 不允许常量可强制转换为对象。 相反，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集定义为参数<xref:System.IntPtr>类型。</xref:System.IntPtr>  
  
 这些方法中的托管的实现应利用这一事实，<xref:System.IntPtr>类同时具有`int`和`void *`构造函数可创建<xref:System.IntPtr>从一个对象或整数常量，为相应。</xref:System.IntPtr> </xref:System.IntPtr>  
  
 托管方法接收<xref:System.IntPtr>此类型的参数应该使用<xref:System.IntPtr>类型转换运算符来处理结果。</xref:System.IntPtr> </xref:System.IntPtr> 第一次转换<xref:System.IntPtr>到`int`和测试针对相关的整数常量。</xref:System.IntPtr> 如果任何值不匹配，将其转换为所需类型的对象，并继续。  
  
 有关此操作的示例，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 返回的值作为传递 [out] 参数  
 查找具有的方法的`retval`中 COM 接口，但返回值具有`int`返回值和附加 [out] 中的数组参数[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。 现在应该很清楚这些方法需要特殊处理，因为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型有一个比 COM 接口方法的多个参数。  
  
 许多 OLE 活动处理的 COM 接口将 OLE 状态的信息发送回调用程序存储在`retval`返回值的接口。 而不是使用相对应的返回值[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集的方法将信息发送回调用程序存储在 [out] 一个数组参数。  
  
 这些方法中的托管的实现应创建作为 [out] 参数的相同类型的单元素数组，并将其放在参数中。 数组元素的值应为与相应 COM 相同`retval`。  
  
 调用此类型的接口的托管的方法应请求从 [out] 的数组的第一个元素。 可以将此元素处理，就好像`retval`从相应的 COM 接口返回值。  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
