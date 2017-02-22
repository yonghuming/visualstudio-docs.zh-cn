---
title: "移动性警告 | Microsoft Docs"
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
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "托管代码分析警告, 移动性警告"
  - "移动性警告"
  - "警告, 移动性"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 移动性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

移动性警告支持高效使用电源。  
  
## 本节内容  
  
|规则|说明|  
|--------|--------|  
|[CA1600：不要使用 Idle 进程优先级](../code-quality/ca1600-do-not-use-idle-process-priority.md)|不要将进程优先级设置为 Idle。  具有 System.Diagnostics.ProcessPriorityClass.Idle 优先级的进程将在 CPU 本应处于空闲状态时占用它，从而阻止进入待机状态。|  
|[CA1601：不要使用阻止电源状态更改的计时器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|频率较高的定期活动会使 CPU 处于繁忙状态，并且会干扰具有节能功能（关闭显示器和硬盘）的空闲计时器。|