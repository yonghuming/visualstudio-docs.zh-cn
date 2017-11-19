---
title: "CA1823： 避免未使用的私有字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f4be67d74c3b0b01092d43d70c3c37a776def14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823：避免未使用的私有字段
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 你的代码中的私有字段存在，但不是使用任何代码路径时，将报告此规则。  
  
## <a name="rule-description"></a>规则说明  
 检测到程序集内有似乎未访问过的私有字段。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请删除该字段或添加使用它的代码。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1812：避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801：检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)