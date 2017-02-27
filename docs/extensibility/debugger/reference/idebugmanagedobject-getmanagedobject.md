---
title: "IDebugManagedObject::GetManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::GetManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::GetManagedObject 方法"
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回表示托管对象的接口。  
  
## 语法  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### 参数  
 `ppManagedObject`  
 \[out\] 返回表示托管对象的接口。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 从此方法返回的接口可为托管类实现的任何接口。查询，允许其方法调用。  
  
## 请参阅  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)