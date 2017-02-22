---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
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
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference 方法"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取对象点。  
  
## 语法  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### 参数  
 `dwIndex`  
 \[in\] 从初始对象的简单字节偏移量点。  
  
 `ppObject`  
 \[out\] 返回一个指向的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象，以及偏移量，因此，如果有的话\)。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  ，如果该对象不指向另一个对象，返回 E\_FAIL。  
  
## 备注  
 点的对象可以是基元或复杂类型 \(如类或结构。  
  
## 请参阅  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)