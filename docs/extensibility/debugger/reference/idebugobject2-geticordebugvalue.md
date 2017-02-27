---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugObject2::GetICorDebugValue 方法"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取表示值的托管代码对象与此对象关联的。  
  
## 语法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### 参数  
 `ppUnk`  
 \[out\] 表示此别名的 `IUnknown` 接口。  此接口可用于 `ICorDebugValue` 接口中查询。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 `ICorDebugValue` 对象是表示值的公共语言运行时接口。  
  
## 请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)