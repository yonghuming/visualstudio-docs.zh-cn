---
title: "CA2219： 不会引发异常子句中的异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da4b337ad0efb3a4876857bd07efb391dc040405
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219：在异常子句中不引发异常
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改中断|  
  
## <a name="cause"></a>原因  
 从引发异常`finally`，筛选器或 fault 子句。  
  
## <a name="rule-description"></a>规则说明  
 当在异常子句中引发了异常时，则会大大增加调试的难度。  
  
 在引发异常时`finally`或 fault 子句，新异常将隐藏活动异常，如果存在。 这使得难以检测和调试原始错误。  
  
 当筛选器子句中引发了异常时，则运行时将以无提示方式捕获异常，并导致筛选器计算结果为 false。 没有方法来判断计算为 false，并且从筛选器引发的异常的筛选器之间的差异。 这使得很难检测和调试中的筛选器的逻辑错误。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要解决此冲突的此规则，不显式会引发异常`finally`，筛选器或 fault 子句。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则的警告。 在任何的情况都在其下的异常子句中引发的异常提供对执行代码的一个好处。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1065：不要在意外的位置引发异常](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>另请参阅  
 [设计警告](../code-quality/design-warnings.md)