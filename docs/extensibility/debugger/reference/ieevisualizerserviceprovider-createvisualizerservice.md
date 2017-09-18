---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService 方法"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法将创建一个可视化工具服务。  
  
## 语法  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### 参数  
 `binder`  
 \[in\] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 对象传递给 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  
  
 `pSymProv`  
 \[in\] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 对象传递给 `IDebugParsedExpression::EvaluateSync`。  
  
 `pAddress`  
 \[in\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象传递给 `IDebugParsedExression::EvaluateSync`。  
  
 `dataProvider`  
 \[in\] 实现 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 接口的对象 \(提供的表达式计算器\)。  
  
 `ppService`  
 \[out\] 创建的服务。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 `binder`、 `pSymProv`和 `pAddress` 所有参数传递给 `IDebugParsedExpression::EvaluateSync` 方法。  `CreateVisualizerService` 将从 `IDebugParsedExpression::EvaluateSync` 仅调用作为表达式计算器的一部分进行类型可视化工具支持。  
  
## 请参阅  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)