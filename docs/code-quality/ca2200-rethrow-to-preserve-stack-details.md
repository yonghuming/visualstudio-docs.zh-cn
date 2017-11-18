---
title: "CA2200： 再次引发以保留堆栈详细信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca2e6e61b88d4d8aaccd4784e1b521e0cbb48bd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200：再次引发以保留堆栈详细信息
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 重新引发异常并在显式指定了该异常`throw`语句。  
  
## <a name="rule-description"></a>规则说明  
 引发异常，携带的信息的一部分后的堆栈跟踪。 将堆栈跟踪信息的方法调用层次结构的开头的方法引发异常和结束的捕获异常的方法列表。 如果通过指定中的异常重新引发异常`throw`语句，在当前方法中重新启动的堆栈跟踪和引发异常的原始方法与当前方法之间的方法调用列表将丢失。 若要保留与该异常的原始堆栈跟踪信息，使用`throw`而无需指定异常的语句。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，重新而无需显式指定异常引发异常。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示一种方法， `CatchAndRethrowExplicitly`，这违反了规则和方法， `CatchAndRethrowImplicitly`，以及满足该规则。  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]