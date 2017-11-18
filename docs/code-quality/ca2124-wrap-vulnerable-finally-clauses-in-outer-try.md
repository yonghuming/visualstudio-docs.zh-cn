---
title: "CA2124： 包装易受攻击在外部 try 块 finally 子句 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f4d30a07ed0930d5165629f7c4b468d7e5146613
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124：在外部 try 块中包装易受攻击的 finally 子句
|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 在 1.0 和 1.1 版的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，公共或受保护的方法包含`try` / `catch` / `finally`块。 `finally`块似乎要重置安全状态，并且不包括在`finally`块。  
  
## <a name="rule-description"></a>规则说明  
 此规则就会查找`try` / `finally`在面向版本 1.0 和 1.1 的代码中的块[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可能容易受到恶意异常筛选器调用堆栈中存在。 如果敏感的操作，如模拟出现在 try 块中，且会引发异常，筛选器可以执行之前`finally`块。 对于模拟示例中，这意味着筛选器将执行与模拟用户。 筛选器是仅在 Visual Basic 中当前实施。  
  
> [!WARNING]
>  **请注意**2.0 及更高版本的版本中[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，运行时自动保护`try` / `catch` /  `finally`重置发生的情况下阻止从恶意异常筛选器直接在方法内包含的异常块。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 放置解包`try` / `finally`外部 try 块中。 请参阅下面的第二个示例。 这将强制`finally`筛选器代码之前执行。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="pseudo-code-example"></a>伪代码示例  
  
### <a name="description"></a>描述  
 下面伪代码说明此规则检测到的模式。  
  
### <a name="code"></a>代码  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## <a name="example"></a>示例  
 下面的伪代码演示的模式可用于保护你的代码和满足此规则。  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```