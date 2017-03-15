---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回代码上下文对象具有指定的代码位置标识符相对应。  
  
## 语法  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### 参数  
 `uCodeLocationId`  
 \[in\] 指定代码位置标识符。  为代码位置标识符的声明中 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) 方法参见 " 备注 " 节。  
  
 `ppCodeContext`  
 \[out\] 返回表示关联的代码上下文的 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 代码位置标识符从调用返回到 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) 方法，并可以出现在 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 结构。  
  
 若要将代码上下文为代码位置标识符，请调用 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) 方法。  
  
## 请参阅  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)