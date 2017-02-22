---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

调用函数并返回得到的值为对象。  
  
## 语法  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### 参数  
 `ppParams`  
 \[in\] 表示输入参数的数组 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象。  这些参数的每一个是使用其中一个方法创建此接口。  
  
 `dwParams`  
 \[in\] 的参数数量。 `ppParams` 数组。  
  
 `dwEvalFlags`  
 \[in\] 指定标志的组合。 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举的计算方式执行。  
  
 `dwTimeout`  
 \[in\] 以毫秒为单位指定最长时间，因此，在返回等待来自此方法。  使用 **无限** 会无限期地等待。  
  
 `ppResult`  
 \[out\] 返回表示函数的值作为对象的 **IDebugObject** 。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)