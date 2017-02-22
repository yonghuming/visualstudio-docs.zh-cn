---
title: "表达式计算器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "表达式 [调试 SDK]"
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 表达式计算器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

，当 IDE 处于中断模式时，表达式计算器 \(EE\)检查语言的语法分析和计算变量与表达式在运行时，从而使它们由用户查看。  
  
## 使用 " 表达式计算器  
 使用 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法，表达式创建，如下所示:  
  
1.  调试引擎 \(DE\) [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 实现接口。  
  
2.  调试包从 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 接口获取 `IDebugExpressionContext2` 对象并调用此操作的 `IDebugStackFrame2::ParseText` 方法获取 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 对象。  
  
3.  调试打包名为 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 方法或 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 方法获取该表达式的值。  `IDebugExpression2::EvaluateAsync` 从命令\/即时窗口调用。  其他 UI 元素调用 `IDebugExpression2::EvaluateSync`。  
  
4.  表达式计算结果为 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 对象，包含表达式计算结果的名称、类型和值。  
  
 在计算表达式时， EE 需要从符号提供程序元素的信息。  符号提供程序提供确定并了解已分析的表达式使用的符号信息。  
  
 在异步表达式计算完成时，异步操作由 DE 发送通过会议调试管理器 \(SDM\)通知 IDE 表达式计算完成。  当同步表达式计算完成时，计算的结果从调用返回到 `IDebugExpression2::EvaluateSync` 方法。  
  
## 实现批注  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试引擎应该使用公共语言运行时接口的表达式计算器 \(CLR\)连接。  因此，与 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用的表达式计算器调试引擎必须支持 CLR \(完整的所有 CLR 调试接口可在 debugref.doc 找到，是 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]的一部分\)。  
  
## 请参阅  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)