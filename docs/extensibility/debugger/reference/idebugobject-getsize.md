---
title: "IDebugObject::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetSize"
helpviewer_keywords: 
  - "IDebugObject::GetSize 方法"
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在字节获取对象的大小。  
  
## 语法  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### 参数  
 `pnSize`  
 \[out\] 在字节返回的大小。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 使用 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) 方法检索值作为字节序列。  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)