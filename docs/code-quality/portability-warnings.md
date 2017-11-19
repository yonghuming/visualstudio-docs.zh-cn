---
title: "可移植性警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 112f3686f2a3d21b2d5d493498b42e9b63fdb05b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="portability-warnings"></a>可移植性警告
可移植性警告支持跨不同操作系统的可移植性。  
  
## <a name="in-this-section"></a>本节内容  
  
|规则|描述|  
|----------|-----------------|  
|[CA1900：值类型字段应为可移植字段](../code-quality/ca1900-value-type-fields-should-be-portable.md)|此规则检查： 当用显式布局特性声明的结构封送到 64 位操作系统上的非托管代码时，将是否正确对齐。|  
|[CA1901: P/Invoke 声明应为可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|此规则计算 P/Invoke，返回值和每个参数的大小，并验证它们的大小正确封送到 32 位和 64 位操作系统上的非托管代码时。|  
|[CA1903：仅使用目标框架中的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|一个成员或类型使用了某个 Service Pack 中引入的成员或类型，该 Service Pack 没有与项目的目标框架一起包括。|