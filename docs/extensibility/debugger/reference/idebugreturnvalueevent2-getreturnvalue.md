---
title: "IDebugReturnValueEvent2::GetReturnValue | Microsoft Docs"
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
  - "IDebugReturnValueEvent2::GetReturnValue"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReturnValueEvent2::GetReturnValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在单步执行获取返回的值设置为在或功能之外。  
  
## 语法  
  
```cpp#  
HRESULT GetReturnValue (   
   IDebugProperty2** ppReturnValue  
);  
```  
  
```c#  
int GetReturnValue (   
   out IDebugProperty2 ppReturnValue  
);  
```  
  
#### 参数  
 `ppReturnValue`  
 \[out\] 返回表示要检索的值的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)