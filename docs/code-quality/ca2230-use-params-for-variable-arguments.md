---
title: "CA2230： 对变量自变量使用 params |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10920c4ff9083b52e2d35f7fa151644b89bb1102
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230：对可变数量的自变量使用 params
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|类别|Microsoft.Usage|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型包含使用一个公共或受保护方法`VarArgs`调用约定。  
  
## <a name="rule-description"></a>规则说明  
 `VarArgs`调用约定使用具有某些方法定义的采用数量可变的参数。 方法使用`VarArgs`调用约定不是公共语言规范 (CLS) 符合，并且可能无法访问跨编程语言。  
  
 在 C# 中，`VarArgs`时该方法的参数列表的结束与调用约定使用`__arglist`关键字。 Visual Basic 不支持`VarArgs`调用约定和 Visual c + + 使用椭圆的非托管代码中仅允许其使用`...`表示法。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，在 C# 中，使用[params](/dotnet/csharp/language-reference/keywords/params)关键字而不是`__arglist`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示两种方法，一个与该规则冲突，一个满足该规则。  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [语言独立性和与语言无关的组件](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)