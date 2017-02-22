---
title: "EVALFLAGS | Microsoft Docs"
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
  - "EVALFLAGS"
helpviewer_keywords: 
  - "EVALFLAGS 枚举"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定控制表达式计算的标志。  
  
## 语法  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## 成员  
 EVAL\_RETURNVALUE  
 指定返回值，如果有，则计算。  
  
 EVAL\_NOSIDEEFFECTS  
 指定副作用不允许。  
  
 EVAL\_ALLOWBPS  
 停止的标识在断点。  
  
 EVAL\_ALLOWERRORREPORT  
 指定错误报告给将允许的。  主要用于表达式计算在脚本在 Internet Explorer。  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 军队的优点函数会计算为地址，而不是调用该函数。  
  
 EVAL\_NOFUNCEVAL  
 防止函数进行求值。  例如，请考虑在表达式 `myExpression(int) + 10`的 `int` 标记。  此功能能被正确计算为地址，但是，不是值。  
  
 EVAL\_NOEVENTS  
 指示标志。表达式计算期间发生的事件不应发送到该会话调试管理器 \(SDM\)或对 IDE。  
  
## 备注  
 这些标志将作为参数传递 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 和 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 方法。  
  
 这些标志可以按位组合使用或。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)