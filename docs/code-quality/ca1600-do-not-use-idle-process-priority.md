---
title: "CA1600：不要使用 Idle 进程优先级 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600：不要使用 Idle 进程优先级
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|类别|Microsoft.Mobility|  
|是否重大更改|是|  
  
## 原因  
 当进程设置为 `ProcessPriorityClass.Idle` 时，将引发此规则。  
  
## 规则说明  
 不要将进程优先级设置为 Idle。  具有 `System.Diagnostics.ProcessPriorityClass.Idle` 优先级的进程将在 CPU 本应处于空闲状态时占用它，从而阻止进入待机状态。  
  
## 如何解决冲突  
 将进程设置为 `ProcessPriorityClass.BelowNormal`。  
  
## 何时禁止显示警告  
 只有当 Idle 进程优先级是必需的，而且可以安全地忽略移动性注意事项时，才应禁止显示此规则。