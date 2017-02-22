---
title: "IDebugFunctionPosition2 | Microsoft Docs"
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
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "IDebugFunctionPosition2 接口"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示函数的抽象位置在源文档。  
  
## 语法  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示一个函数的位置中的源文档。  
  
## 调用方的说明  
 此接口中提供作为 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 联合的一部分 \(特别是， [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 结构\) 又作为 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) framework 的一部分，用于创建挂起的断点。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugFunctionPosition2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|获取函数的名称此相对位置。|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|获取偏移量最初函数。|  
  
## 备注  
 此接口表示的该位置是基于文本，具体而言， [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 结构。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)