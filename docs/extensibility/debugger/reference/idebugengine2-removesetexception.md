---
title: "IDebugEngine2::RemoveSetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveSetException"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveSetException"
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

移除指定的异常，因此它由调试引擎不再处理。  
  
## 语法  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### 参数  
 `pException`  
 \[in\] 描述要移除的异常的 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 必须由之前设置移除的异常之前调用对 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 方法。  
  
 立即移除所有设置的异常，请调用 [RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md) 方法。  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)