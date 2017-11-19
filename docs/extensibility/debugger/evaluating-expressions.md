---
title: "计算表达式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 870469b77eb2f9fcf562602dd651c84fa71020ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-expressions"></a>计算表达式
表达式是从字符串向下传递，从自动、 监视、 快速监视，或即时窗口中创建的。 计算表达式，则它会生成一个可打印字符串，包含的名称和类型的变量或自变量和其值。 此字符串显示在相应的 IDE 窗口中。  
  
## <a name="implementation"></a>实现  
 当程序在断点处停止时计算的表达式。 该表达式本身由[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口，表示可供绑定和评估在给定的表达式评估上下文中的已分析的表达式。 堆栈帧确定表达式评估上下文，通过实现提供的调试引擎 (DE) [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。  
  
 给定用户字符串和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口，可以获取调试引擎 (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口的用户将字符串传递到[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 返回的 IDebugExpression2 接口包含准备好进行评估的已分析的表达式。  
  
 与`IDebugExpression2`接口，DE 可以获取通过同步或异步表达式计算、 表达式的值使用[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。 显示的情况下，此值的名称和类型的变量或参数，以及发送到 IDE。 值、 名称和类型由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)接口。  
  
 若要启用表达式求值，DE 必须实现[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口。 同步和异步评估要求实现[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)