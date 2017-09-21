---
title: "IDebugProperty3::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取自定义浏览器列表与此属性关联。  
  
## 语法  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### 参数  
 `celtSkip`  
 \[in\] 跳过浏览器的数量。  
  
 `celtRequested`  
 \[in\] 检索浏览器的数 \(还指定 `rgViewers` 数组的大小\)。  
  
 `rgViewers`  
 \[in, out\] 数组将填充的 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 结构。  
  
 `pceltFetched`  
 \[out\] 返回浏览器的实际数目。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 向前支持类型可视化工具，此方法调用 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 方法。  如果表达式计算器还支持此属性类型的自定义浏览器，此方法会追加相应的自定义浏览器到列表中。  
  
 请参见 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 有关差异的详细信息类型可视化工具和自定义浏览器之间。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 接口的 **CProperty** 对象的方法。  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## 请参阅  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [类型的可视化工具和自定义查看器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)