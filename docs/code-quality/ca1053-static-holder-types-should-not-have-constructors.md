---
title: "CA1053： 静态容器类型不应具有构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9e9d6272fbb21644daab96bb3ccd7d02b023840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053：静态容器类型不应具有构造函数
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或嵌套公共类型只声明了静态成员，但具有公共或受保护的默认构造函数。  
  
## <a name="rule-description"></a>规则说明  
 由于调用静态成员不需要类型的示例，因此没必要使用构造函数。 此外，类型不具有非静态成员，因为创建的实例不提供访问到任何类型的成员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除默认构造函数，或设为专用。  
  
> [!NOTE]
>  如果类型未定义任何构造函数，则某些编译器将自动创建公共默认构造函数。 如果这是你的类型，这种情况，添加一个私有的默认构造函数，以消除冲突。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 存在构造函数提供的建议的类型不是静态类型。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。 请注意在源代码中是没有默认构造函数。 当此代码会编译成程序集时，C# 编译器将插入一个默认构造函数，其将违反此规则。 若要纠正此问题，声明一个私有构造函数。  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]