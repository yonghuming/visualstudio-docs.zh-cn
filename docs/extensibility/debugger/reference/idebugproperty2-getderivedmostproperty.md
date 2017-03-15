---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取属性的派生最的属性。  
  
## 语法  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### 参数  
 `ppDerivedMost`  
 \[out\] 返回表示该派生最的属性的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  ; 如果没有检索，派生的最的属性返回 `S_GETDERIVEDMOST_NO_DERIVED_MOST` 。  
  
## 备注  
 例如，因此，如果此属性描述实际上是 `ClassDerived` 实例化从 `ClassRoot`派生的对象实现 `ClassRoot` ，但，则此方法返回描述 `ClassDerived` 对象的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 对象。  
  
## 请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)