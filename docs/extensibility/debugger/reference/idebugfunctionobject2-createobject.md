---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
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
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建使用给定的构造函数计算标志设置和超时值的对象。  
  
## 语法  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### 参数  
 `pConstructor`  
 \[in\] 表示要创建的对象构造函数的 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 对象。  
  
 `dwArgs`  
 \[in\] 的参数数量。 `pArg` 数组。  表示参数的数目传递给构造函数。  
  
 `pArgs`  
 \[in\] 表示参数的数组 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象传递给构造函数。  
  
 `dwEvalFlags`  
 \[in\] 指定标志的组合。 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 枚举的计算方式执行。  
  
 `dwTimeout`  
 \[in\] 最长时间，以毫秒为单位，在返回等待来自此方法。  使用 **无限** 会无限期地等待。  
  
 `ppObject`  
 \[out\] 返回表示新创建的对象的 **IDebugObject** 。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 调用此方法创建表示类实例对象，或者需要构造函数，为参数的其他复杂类型。  
  
## 请参阅  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)