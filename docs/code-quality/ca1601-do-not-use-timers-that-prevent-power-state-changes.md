---
title: "CA1601： 不要使用阻止电源状态更改的计时器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fc42c15beda68472f4a980fe96b0055b70a01cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601：不要使用阻止电源状态更改的计时器
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|类别|Microsoft.Mobility|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 计时器的间隔设置为发生每秒的不止一次。  
  
## <a name="rule-description"></a>规则说明  
 不执行频率高于每秒或发生的频率高于一个使用计时器一次轮询时间每秒。 频率较高的定期活动会使 CPU 处于繁忙状态，并且会干扰具有节能功能（关闭显示器和硬盘）的空闲计时器。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 设置计时器时间间隔发生每秒不超过一次。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 应禁止显示此规则，仅当是必需的触发计时器每秒的不止一次且可以安全地忽略移动性注意事项。