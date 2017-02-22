---
title: "IDebugObject::SetReferenceValue | Microsoft Docs"
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
  - "IDebugObject::SetReferenceValue"
helpviewer_keywords: 
  - "IDebugObject::SetReferenceValue 方法"
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

将此对象的引用值。  
  
## 语法  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```c#  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### 参数  
 `pObject`  
 \[in\] 表示新 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象引用值。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 此方法使此 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象对在 `pObject` 参数为对象的值，引发的任何以前的引用。  请注意此 `IDebugObject` 对象必须已引用类型。  
  
## 请参阅  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)