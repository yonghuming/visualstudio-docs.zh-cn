---
title: "表达式计算上下文 | Microsoft Docs"
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
  - "表达式计算、 上下文"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 表达式计算上下文
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在调试的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ， **表达式计算上下文**:  
  
-   表示表达式计算的上下文。  通常，计算上下文对应于中计算变量、参数、函数和方法的词法范围。  例如，表达式计算上下文与堆栈帧为计算的局部变量、方法参数和类成员将提供上下文 \(如果适用\)。  
  
-   ，当程序在断点处停止后，存在。  是一个表示准备绑定和计算在给定上下文中的一个分析表达式的数据结构。  
  
     更详细地，使用 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法，表达式创建。  在计算表达式时，它会生成包含名称和类型的变量个可打印的字符串或参数及其值。  此字符串显示在 " 监视 " 窗口或在 IDE 的本地窗口。  
  
     命名 `BSTR` 和 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 接口，调试引擎 \(DE\)可以通过分析表达式创建 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 接口。  命名 `IDebugExpression2` 接口， DE 通过同步或异步计算表达式可以获取值。  此值，与变量或参数。的名称和类型，发送到显示的 IDE。  
  
## 请参阅  
 [表达式计算接口](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)