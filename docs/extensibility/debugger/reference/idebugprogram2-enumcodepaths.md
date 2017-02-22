---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
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
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索代码路径的列出给定位置的源文件。  
  
## 语法  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### 参数  
 `pszHint`  
 \[in\] 在光标之下的单词在 IDE 的 **源** 或 **反汇编** 视图。  
  
 `pStart`  
 \[in\] 表示当前代码上下文的 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 对象。  
  
 `pFrame`  
 \[in\] 表示堆栈帧的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 对象与当前断点。  
  
 `fSource`  
 \[in\] 非零 \(`TRUE`\)，如果在 **源** 视图或零 \(0\)`FALSE`\)，如果在 **反汇编** 视图。  
  
 `ppEnum`  
 \[out\] 返回包含代码路径的列表 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) 对象。  
  
 `ppSafety`  
 \[out\] 但是，如果选定的代码路径跳过，返回表示一个附加代码上下文的 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 对象将设置为断点。  则会发生后一个短路的布尔表达式，。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 代码路径描述方法的名称或调用获取对当前的功能在程序的执行点。  代码路径列表表示调用堆栈。  
  
## 请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)