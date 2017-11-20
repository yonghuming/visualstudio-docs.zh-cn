---
title: "CA1048： 不要声明在密封类型中的虚拟成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1f4456a65eb78ce64ad4c5bbfb4695ba0da3e64
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048：不要在密封类型中声明虚拟成员
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共类型密封的并声明既是一个方法`virtual`(`Overridable`在 Visual Basic 中) 和不是为最终。 此规则不会报告冲突，必须遵循此模式的委托类型。  
  
## <a name="rule-description"></a>规则说明  
 类型将方法声明为虚方法，使继承类型可以重写虚方法的实现。 根据定义，不能继承密封类型，使得虚方法对于密封类型没有意义。  
  
 Visual Basic.NET 和 C# 编译器不允许违反此规则的类型。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使该方法成为非虚方法或使该类型可继承。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 离开在其当前状态的类型可能会导致维护问题并不提供任何好处。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]