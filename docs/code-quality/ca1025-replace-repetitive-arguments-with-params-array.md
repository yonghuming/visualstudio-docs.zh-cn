---
title: "CA1025： 用参数数组替换重复的自变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 910be06a7d9897f306b6bb2b89ca99b733623faf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025：用形参数组替换重复的实参
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共类型中的公共或受保护方法具有三个以上参数，且其最后三个参数为相同的类型。  
  
## <a name="rule-description"></a>规则说明  
 当自变量的具体数量未知且变量自变量具有相同的类型，或可作为相同类型传递，请使用参数数组代替重复参数。 例如，<xref:System.Console.WriteLine%2A>方法提供参数数组用于接受任意数量的通用重载<xref:System.Object>自变量。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将重复的自变量替换参数数组。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则始终可以安全地禁止显示此规则; 的警告但是，这种设计可能会导致可用性问题。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]