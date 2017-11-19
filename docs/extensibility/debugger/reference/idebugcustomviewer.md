---
title: "IDebugCustomViewer |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer
helpviewer_keywords: IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b7d32746fa42dc270497252065c3ac117a59547
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
此接口允许的表达式计算器 (EE) 以显示属性的值是必需的任何格式。  
  
## <a name="syntax"></a>语法  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>实施者注意事项  
 EE 实现此接口可自定义格式显示属性的值。  
  
## <a name="notes-for-callers"></a>调用方的说明  
 调用 COM 的`CoCreateInstance`函数实例化此接口。 `CLSID`传递给`CoCreateInstance`从注册表获取。 调用[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)获取在注册表中的位置。 有关详细信息，以及该示例，请参阅备注。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
 此接口实现以下方法：  
  
|方法|描述|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|会任何执行所需显示的给定的值。|  
  
## <a name="remarks"></a>备注  
 当无法通过常规方法显示属性的值时使用此接口 — 例如，对于数据表或另一种复杂属性类型。 自定义查看器所表示的`IDebugCustomViewer`接口，不同于类型可视化工具，这是用于显示特定类型而不考虑 EE 的数据的外部程序。 EE 实现特定于该 EE 的自定义查看器。 用户选择哪种类型的可视化工具使用，为其类型可视化工具或自定义查看器。 请参阅[Visualizing 和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)有关此过程的详细信息。  
  
 自定义查看器注册 EE 的方式相同，并因此，需要一种语言 GUID 和供应商 GUID。 仅对 EE 是已知的确切度量值 （或注册表项的名称）。 在中返回此指标[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)结构，又通过调用返回[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)。 存储在度量值的值是`CLSID`传递给 COM 的`CoCreateInstance`函数 （请参见示例）。  
  
 [SDK 以便进行调试的帮助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函数， `SetEEMetric`，可以用于注册自定义查看器。 请参阅的"表达式计算器"注册表部分`Debugging SDK Helpers`对于特定的注册表键需要自定义查看器。 请注意，自定义查看器将需要只有一个度量值 （这由 EE 的实施者），而表达式计算器需要多个预定义的指标。  
  
 通常情况下，自定义查看器提供的数据的只读视图由于[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)接口提供给[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)没有方法用于更改除字符串形式的属性的值。 为了支持更改任意数据块，EE 实现自定义接口上实现的相同对象`IDebugProperty3`接口。 然后，此自定义接口将提供更改数据的任意块所需的方法。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>示例  
 此示例演示如何从属性获取第一个自定义查看器，如果该属性具有任何自定义查看器。  
  
```cpp  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK 适用于调试的帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)