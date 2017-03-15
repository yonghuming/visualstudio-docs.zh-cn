---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService 方法"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法返回请求的服务。  
  
## 语法  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### 参数  
 `vendor`  
 \[in\] 供应商的 `GUID` \(null 值可接受\)。  
  
 `language`  
 \[in\] 语言的 `GUID` \(null 值可接受\)。  
  
 `iid`  
 \[in\] 获取的服务的 `IID` 。  
  
 `ppService`  
 \[out\] 所请求的服务的接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 通过 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) 接口 \(`IID_IEEVisualizerServiceProvider`\) `IID` 发现类型可视化工具服务是否可用。  如果是这样，表达式计算器能够获取 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 接口支持类型可视化工具。  有关详细信息，请参见[可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [可视化和查看数据](../../../extensibility/debugger/visualizing-and-viewing-data.md)