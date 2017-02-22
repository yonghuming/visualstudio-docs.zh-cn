---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
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
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject 方法"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在调试引擎的地址空间创建托管对象的副本。  
  
## 语法  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### 参数  
 `ppObject`  
 \[out\] 返回表示新创建的托管对象 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  ，如果此 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 不表示托管值类的实例，返回 E\_FAIL。  
  
## 备注  
 此 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象必须表示托管值类实例，如 `System.Decimal` 实例。  由具有本地副本， [评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 消除开销调用。  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)