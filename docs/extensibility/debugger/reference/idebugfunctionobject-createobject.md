---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObject 方法"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用构造函数，创建一个对象。  
  
## 语法  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### 参数  
 `pConstructor`  
 \[in\] 表示对象的构造函数 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 将会创建对象。  
  
 `dwArgs`  
 \[in\] 的参数数量。`pArg` 数组。  表示参数的数目传递给构造函数。  
  
 `pArg`  
 \[in\] 数组表示参数的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象传递给构造函数。  
  
 `ppObject`  
 \[out\] 返回表示新创建的对象的 `IDebugObject` 。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 调用此方法创建表示需要构造函数\) 类的对象 \(或其他复杂类型的实例作为参数传递给由 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口表示的功能。  
  
 如果对象参数不需要构造函数，请调用 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) 方法。  
  
## 请参阅  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)