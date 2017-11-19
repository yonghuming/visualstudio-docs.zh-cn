---
title: "CA1600： 不要使用 idle 进程优先级 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600：不要使用 Idle 进程优先级
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|类别|Microsoft.Mobility|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 进程被设置为时，将引发此规则`ProcessPriorityClass.Idle`。  
  
## <a name="rule-description"></a>规则说明  
 不要将进程优先级设置为 Idle。 进程`System.Diagnostics.ProcessPriorityClass.Idle`将 CPU 时占用它本应处于空闲状态，因此将阻止进入待机状态。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 设置为进程`ProcessPriorityClass.BelowNormal`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 仅当需要 Idle 进程优先级也可以安全地忽略移动性注意事项时，应禁止显示此规则。