---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "IDebugCustomViewer 接口"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许表达式计算器 \(EE\)演示一个属性值在任何格式是必需的。  
  
## 语法  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## 实现者说明  
 EE 实现此接口公开一个属性以自定义格式。  
  
## 调用方的说明  
 对 COM 的 `CoCreateInstance` 函数的调用实例化此接口。  `CLSID` 传递给 `CoCreateInstance` 从注册表中获取。  为 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 的调用获取注册表的位置。  有关详细信息和示例参见备注。  
  
## 方法按 Vtable 顺序  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|执行任何必要显示特定值。|  
  
## 备注  
 此接口，当属性值不能由正常显示方式 \(例如，与数据表或另一个复杂的属性类型时，使用。  自定义浏览器，如由 `IDebugCustomViewer` 接口，类型为可视化工具不同，无论 EE，为要显示的特定类型的数据外部程序。  EE 实现了特定于该 EE 的自定义浏览器。  使用的可视化工具的类型，假如是类型的可视化工具或自定义浏览器用户选择。  请参见 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md) 有关此过程的详细信息。  
  
 自定义浏览器与 EE 的方式注册，因此，因此，需要语言学 GUID 和供应商 GUID。  确切的度量值 \(或注册表访问名\) 才知道到 EE。  此指标在 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) framework 返回，供 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)的调用又返回。  传递给 COM 的 `CoCreateInstance` 功能的度量值存储的值是 `CLSID` \(请参见示例\)。  
  
 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 功能， `SetEEMetric`，可用于注册自定义浏览器。  为自定义浏览器所需的特定注册表项参见 `Debugging SDK Helpers` 的 “表达式计算器”注册表部分。  请注意自定义浏览器只需要一个指标 \(由 EE 的实现定义的\)，而表达式计算器需要几种预定义的指标。  
  
 通常，，因为 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口提供给 [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 没有更改属性值的方法只是为字符串，自定义浏览器发送数据的只读视图。  为了支持更改任意块数据， EE 实现在同一对象的自定义接口实现 `IDebugProperty3` 接口。  此自定义接口然后将提供必要的方法更改任意块数据。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 示例  
 ，如果该属性具有任何自定义浏览器，本示例演示如何从获取属性的第一个自定义浏览器。  
  
```cpp#  
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
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK 帮助器调试](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)