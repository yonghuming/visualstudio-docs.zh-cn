---
title: "CA1601：不要使用阻止电源状态更改的计时器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1601：不要使用阻止电源状态更改的计时器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|类别|Microsoft.Mobility|  
|是否重大更改|是|  
  
## 原因  
 计时器的触发频率设置为高于每秒一次。  
  
## 规则说明  
 不要以高于每秒一次的频率进行轮询或使用触发频率高于每秒一次的计时器。  频率较高的定期活动会使 CPU 处于繁忙状态，并且会干扰具有节能功能（关闭显示器和硬盘）的空闲计时器。  
  
## 如何解决冲突  
 将计时器的触发频率设置为小于每秒一次。  
  
## 何时禁止显示警告  
 只有当要求计时器的触发频率高于每秒一次，而且可以安全地忽略移动性注意事项时，才应禁止显示此规则。