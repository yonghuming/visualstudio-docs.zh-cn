---
title: "可移植性警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "可移植性警告"
  - "托管代码分析警告, 可移植性警告"
  - "警告, 可移植性"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# 可移植性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可移植性警告用于支持跨不同操作系统进行移植。  
  
## 本节内容  
  
|规则|说明|  
|--------|--------|  
|[CA1900：值类型字段应为可移植字段](../code-quality/ca1900-value-type-fields-should-be-portable.md)|此规则对以下项进行检查：当用显式布局特性声明的结构封送到 64 位操作系统上的非托管代码时，是否正确对齐。|  
|[CA1901：P\/Invoke 声明应为可移植声明](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|此规则计算 P\/Invoke 的每个参数和返回值的大小，还验证它们在封送到 32 位和 64 位操作系统上的非托管代码时的大小是否正确。|  
|[CA1903：仅使用目标框架中的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|一个成员或类型使用了某个 Service Pack 中引入的成员或类型，该 Service Pack 没有与项目的目标框架一起包括。|