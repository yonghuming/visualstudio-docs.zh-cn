---
title: "表达式计算上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ac80a3fcf3a7f75be3f23dd1350da047ccbb393
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-context"></a>表达式计算上下文
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试，**表达式评估上下文**:  
  
-   表示为表达式计算的上下文。 通常情况下，评估上下文对应于在其中评估变量、 参数、 函数和方法的词法范围。 例如，与堆栈帧关联的表达式评估上下文将用于评估本地变量、 方法参数和类成员 （如果适用） 提供上下文。  
  
-   当程序已在断点处停止时存在。 该表达式本身是一种数据结构，表示用于绑定和评估在给定的上下文中的已分析的表达式。  
  
     在详细信息，使用创建表达式[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 计算表达式，则它会生成一个包含的名称和类型的变量或自变量和其值的可打印字符串。 在监视窗口中或者在 IDE 的局部变量窗口中，会显示此字符串。  
  
     给定`BSTR`和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)接口，可以创建调试引擎 (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口通过分析表达式。 给定`IDebugExpression2`接口，DE 可以获取一个值，通过同步或异步表达式计算。 显示的情况下，此值的名称和类型的变量或参数，以及发送到 IDE。  
  
## <a name="see-also"></a>另请参阅  
 [表达式评估接口](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)