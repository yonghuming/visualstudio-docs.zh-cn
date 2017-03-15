---
title: "IDebugProgram2::EnumModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumModules"
helpviewer_keywords: 
  - "IDebugProgram2::EnumModules"
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索此程序加载的模块的列表和执行。  
  
## 语法  
  
```cpp#  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回包含模块的列表 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 模块是 DLL 或程序集和通常列表中 **模块** 调试窗口。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)