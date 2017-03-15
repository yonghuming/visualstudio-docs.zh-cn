---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

销毁唯一 ID 与此属性关联，指示调用方不再考虑从其他特性唯一标识此属性。  
  
## 语法  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 如果调试引擎不需要支持属性的唯一 ID \(因为它唯一地在内部已跟踪它们\)，则可以返回此方法的 `E_NOTIMPL` 。  
  
 唯一 ID 将对 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) 方法的调用创建，当调用方为了确保时，此属性在其他属性中唯一标识。  
  
## 请参阅  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)