---
title: "表达式计算器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b08da6a123107d793d522770d44315aaa432dede
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator"></a>表达式计算器
表达式计算器 (EE) 检查语言来分析和在运行时，计算变量和表达式的语法，从而使它们可以在中断模式下 IDE 时由用户查看。  
  
## <a name="using-expression-evaluators"></a>使用表达式计算器  
 表达式在创建使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，如下所示：  
  
1.  调试引擎 (DE) 实现[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。  
  
2.  调试包获取`IDebugExpressionContext2`对象[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)接口，然后调用`IDebugStackFrame2::ParseText`方法以获取[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)对象。  
  
3.  调试包调用[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法或[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法以获取表达式的值。 `IDebugExpression2::EvaluateAsync`从命令中的即时窗口调用。 所有其他用户界面组件调用`IDebugExpression2::EvaluateSync`。  
  
4.  表达式计算的结果是[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)对象，其中包含名称、 类型和表达式的计算结果值。  
  
 在表达式计算过程 EE 要求从符号提供程序组件的信息。 符号提供程序提供用于确定和了解已分析的表达式的符号信息。  
  
 完成异步表达式求值时，异步事件发送的会话调试管理器 (SDM) 通过 DE 以通知 IDE 表达式计算已完成。 完成同步表达式求值时，从调用返回的计算结果`IDebugExpression2::EvaluateSync`方法。  
  
## <a name="implementation-notes"></a>实现说明  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的调试引擎希望与表达式计算器使用公共语言运行时 (CLR) 接口。 因此，表达式计算器适用于[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的调试引擎必须支持 CLR (调试接口的所有 CLR 的完整列表可以位于 debugref.doc，是一部分的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)])。  
  
## <a name="see-also"></a>另请参阅  
 [调试器组件](../../extensibility/debugger/debugger-components.md)