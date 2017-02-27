---
title: "IEnumDebugFields::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Reset"
helpviewer_keywords: 
  - "IEnumDebugFields::Reset 方法"
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugFields::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法重置枚举到第一个元素。  
  
## 语法  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### 参数  
 无  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法调用之后，下调用 [下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md) 返回枚举中的第一个元素。  
  
## 请参阅  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)