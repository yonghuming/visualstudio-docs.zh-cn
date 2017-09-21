---
title: "IDebugPropertyField::GetPropertySetter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField::GetPropertySetter"
helpviewer_keywords: 
  - "IDebugPropertyField::GetPropertySetter 方法"
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取设置属性的方法。  
  
## 语法  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```c#  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### 参数  
 `ppField`  
 \[out\] 返回表示设置属性的方法的 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则返回错误代码。  
  
## 备注  
 获取获取属性的方法中，调用 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) 方法。  
  
## 请参阅  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)