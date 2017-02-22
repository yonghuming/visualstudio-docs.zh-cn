---
title: "IDebugBinder::Bind | Microsoft Docs"
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
  - "IDebugBinder::Bind"
helpviewer_keywords: 
  - "IDebugBinder::Bind 方法"
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取包含符号的当前值的内存上下文或对象。  
  
## 语法  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### 参数  
 `pContainer`  
 \[in\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 包含的子项由 `pField`引用。  
  
 `pField`  
 \[in\] 表示符号 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。  
  
 `ppObject`  
 \[out\] 返回表示符号实例的 `IDebugObject` 。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)