---
title: "CA2200：再次引发以保留堆栈详细信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2200：再次引发以保留堆栈详细信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 异常被再次引发，在 `throw` 语句中显式指定了该异常。  
  
## 规则说明  
 一旦引发异常，则该异常所携带的信息中有一部分为堆栈跟踪。  堆栈跟踪是方法调用层次结构的列表，以引发该异常的方法开始，以捕捉该异常的方法结束。  如果通过在 `throw` 语句中指定异常来重新引发该异常，则会在当前方法中重新启动堆栈跟踪，引发该异常的原始方法与当前方法之间的方法调用的列表将丢失。  若要保留该异常的原始堆栈跟踪信息，请在使用 `throw` 语句时不要指定该异常。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请在未显式指定异常的情况下再次引发异常。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的方法 `CatchAndRethrowExplicitly` 以及满足该规则的方法 `CatchAndRethrowImplicitly`。  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]