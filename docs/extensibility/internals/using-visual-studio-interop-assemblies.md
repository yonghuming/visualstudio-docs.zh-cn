---
title: "使用 Visual Studio 互操作程序集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 298caf0b1c65ecb3612b927859b4d7d01720fc27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio 互操作程序集
Visual Studio 互操作程序集允许访问提供 Visual Studio 扩展性的 COM 接口的托管应用程序。 有一些直 COM 接口和其互操作的版本之间的差异。 例如，Hresult 通常表示为一个整数值和需要为例外，相同的方式处理和 (尤其是 out 参数） 的参数的处理方式不同。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>处理从 COM 返回到托管代码的 HRESULT  
 当从托管代码调用 COM 接口时，请检查 HRESULT 值并根据需要引发异常。 <xref:Microsoft.VisualStudio.ErrorHandler>类包含<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>方法，将引发 COM 异常，具体取决于的 HRESULT 值传递给它。  
  
 默认情况下，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>都会传递的值小于零的 HRESULT 引发异常。 在此类 Hresult 是可接受的值，其中应不引发任何异常的情况下，应将其他 HRESULT 的值传递给<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>值进行测试后。 如果所测试的 HRESULT 与显式传递到任何 HRESULT 值匹配<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>，不会引发异常。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>类包含常量用于常见的 HRESULT，例如，<xref:Microsoft.VisualStudio.VSConstants.S_OK>和<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]HRESULT，例如，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants>此外提供了<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>和<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>方法，它们分别对应于 COM 中的成功和失败宏  
  
 例如，考虑以下函数调用中，<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>是可接受的返回值，而其他 HRESULT 小于零表示错误。  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 如果有多个可接受的返回值，只可以将其他 HRESULT 值追加到在调用列表<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>从托管代码将 HRESULT 返回到 COM  
 如果不发生任何异常，托管代码返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>向调用它的 COM 函数。 COM 互操作支持托管代码中强类型化的常见异常。 例如，收到不可接受的方法`null`自变量引发<xref:System.ArgumentNullException>。  
  
 如果您不能确定哪个异常引发，但知道 HRESULT 你想要返回到 COM，你可以使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>方法会引发相应的异常。 之所以即使使用非标准错误，例如， <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>尝试的 HRESULT 映射传递给它对强类型异常。 如果无法映射，它会改为引发一般的 COM 异常。 最终结果是，HRESULT 传递给<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>从托管代码返回到调用它的 COM 函数。  
  
> [!NOTE]
>  异常会降低性能，它用于指示程序的异常状况。 对于所发生的状况，通常应以内联方式处理，而不是引发异常。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 参数作为类型 void * * 传递  
 [Out] 定义为类型的参数查找`void **`在 COM 接口，但定义为`[``iid_is``]`中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。  
  
 有时，COM 接口生成`IUnknown`对象和 COM 接口然后将其作为传递类型`void **`。 这些接口是特别重要因为如果变量指 [out] 在 IDL，则`IUnknown`对象是使用引用计数`AddRef`方法。 如果对象不能正确处理，则会发生内存泄漏。  
  
> [!NOTE]
>  `IUnknown`创建的 COM 接口和一个 [out] 变量中返回的对象如果未显式释放会导致内存泄漏。  
  
 处理此类对象的托管的方法应将<xref:System.IntPtr>作为指向的`IUnknown`对象，并调用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法来获取该对象。 然后，调用方应强制转换到任何类型适合的返回值。 当不再需要该对象时，调用<xref:System.Runtime.InteropServices.Marshal.Release%2A>释放它。  
  
 下面是一个示例调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法和处理`IUnknown`正确对象：  
  
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
>  已知的以下方法传递`IUnknown`作为类型对象指针<xref:System.IntPtr>。 本部分中所述处理它们。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out 一个] 可选参数  
 查找定义为 [out] 的参数数据类型 (`int`， `object`，依次类推) 在 COM 接口，但定义为在相同的数据类型的数组[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。  
  
 某些 COM 接口，如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，将 [out] 参数为可选。 如果对象不是必需的这些 COM 接口返回`null`作为该参数而不是创建 [out] 对象的值的指针。 这是设计使然。 这些接口，`null`指针被假定为 VSPackage，正确行为的一部分，而不会返回错误。  
  
 因为 CLR 不允许的值为一个 [out] 参数`null`，这些接口的设计行为的一部分直接在中不可用托管代码。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受影响的接口的互操作程序集方法要解决此问题通过作为数组定义的相关参数，因为 CLR 允许传递的`null`数组。  
  
 这些方法的托管的实现应该`null`到时无需进行任何要返回的参数数组。 否则为创建正确类型的一个元素数组和返回值置于数组中。  
  
 管理从具有可选 [out] 一个接口接收信息的方法参数将参数接收为数组。 只需检查数组的第一个元素的值。 如果不是`null`，将第一个元素，就像它是原始的参数。  
  
## <a name="passing-constants-in-pointer-parameters"></a>指针参数中传递常量  
 查找的参数定义为 [in] COM 接口中的指针使用但定义为<xref:System.IntPtr>键入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。  
  
 在 COM 接口传递的特殊值，如 0、-1 或-2，而不是一个对象指针时，会出现类似问题。 与不同[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]，CLR 不允许可强制转换为对象的常量。 相反，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集定义为参数<xref:System.IntPtr>类型。  
  
 这些方法的托管的实现应充分利用这一事实，<xref:System.IntPtr>类同时具有`int`和`void *`构造函数来创建<xref:System.IntPtr>从对象或一个整型常数，根据需要。  
  
 托管方法接收<xref:System.IntPtr>此类型的参数应使用<xref:System.IntPtr>类型转换运算符来处理结果。 首先将转换<xref:System.IntPtr>到`int`并针对相关的整数常量进行测试。 如果任何值不匹配，将其转换为所需的类型的对象，并继续。  
  
 此示例，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 返回的值作为传递 [out] 参数  
 查找具有的方法的`retval`返回值中的 COM 接口，但具有`int`返回值和附加 [out] 中的数组参数[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型。 应该已经很明确这些方法需要特殊处理，因为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法原型具有比 COM 接口方法的一个更多参数。  
  
 许多 OLE 活动处理的 COM 接口将 OLE 状态有关的信息发送回调用程序存储在`retval`返回的接口的值。 而不是使用相对应的返回值[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互操作程序集方法将信息发送回调用程序存储在 [out] 一个数组参数。  
  
 这些方法的托管的实现应创建与 [out] 参数属于相同类型的单个元素数组，并将其放在参数中。 数组元素的值应为与相应的 COM 相同`retval`。  
  
 调用此类型的接口的托管的方法应提取出 [out] 的数组的第一个元素。 可以处理此元素，就像它是`retval`从相应的 COM 接口返回值。  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)