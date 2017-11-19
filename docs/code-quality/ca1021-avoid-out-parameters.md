---
title: "CA1021： 避免使用 out 参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbefcb83efbcea76fec889b520f0cd0dd181bf9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021：避免使用 out 参数
|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共类型中的公共或受保护方法具有`out`参数。  
  
## <a name="rule-description"></a>规则说明  
 通过引用传递类型 (使用`out`或`ref`) 要求具有使用指针，了解值类型和引用类型的不同之处，以及能处理具有多个返回值的方法的经验。 此外，之间的差异`out`和`ref`参数没有得到广泛了解。  
  
 当"按引用"传递引用类型时，该方法将希望使用参数可返回对象的不同实例。 通过引用传递引用类型也称为使用双指针、 指向指针的指针或双间接寻址。 通过使用默认调用约定，传递"的值"，已采用引用类型的参数接收指向对象的指针。 通过值进行传递指针，它指向的而非对象。 传递值意味着，该方法不能更改要将其指向引用类型的新实例的指针。 但是，它可以更改它所指向的对象的内容。 对于大多数应用程序这就足够了，并生成所需的行为。  
  
 如果方法必须返回不同的实例，请使用方法的返回值来实现此目的。 请参阅<xref:System.String?displayProperty=fullName>各种不同的方法对字符串进行操作并返回一个字符串的新实例的类。 当使用此模型时，调用方必须决定是否保留原始对象。  
  
 尽管返回值比较常见并大量使用正确的应用程序的`out`和`ref`参数需要中间设计和编码技能。 用户设计的一般不应指望用户能熟练运用到库架构师`out`或`ref`参数。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与由值类型导致此规则的冲突，使该方法返回的对象作为其返回值。 如果该方法必须返回多个值，重新设计其返回存储值的对象的单个实例。  
  
 若要修复与由引用类型导致此规则的冲突，请确保所需的行为，是返回引用的新实例。 如果是，该方法应使用其返回值要这样做。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告。 但是，这种设计可能会导致可用性问题。  
  
## <a name="example"></a>示例  
 以下库将显示一个生成的用户反馈响应类的两个实现。 第一个实现 (`BadRefAndOut`) 强制库用户管理三个返回值。 第二种实现 (`RedesignedRefAndOut`) 返回容器类的实例，从而简化用户体验 (`ReplyData`) 管理的数据作为单个单元。  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## <a name="example"></a>示例  
 以下应用程序演示了用户的体验。 重新设计的库的调用 (`UseTheSimplifiedClass`方法) 是更为简单，并轻松地管理由方法返回的信息。 这两种方法的输出是相同的。  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## <a name="example"></a>示例  
 下面的示例库阐释如何`ref`对于引用类型参数使用，并演示更好的方法来实现此功能。  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## <a name="example"></a>示例  
 下面的应用程序中的库，为了演示此行为调用每个方法。  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 本示例生成以下输出。  
  
 **更改指针的按值传递：**  
**12345**  
**12345**  
**更改指针的按引用传递：**  
**12345**  
**12345 ABCDE**  
**通过返回的值进行传递：**  
**12345 ABCDE**   
## <a name="try-pattern-methods"></a>请尝试模式方法  
  
### <a name="description"></a>描述  
 实现的方法**重\<内容 >**模式，如<xref:System.Int32.TryParse%2A?displayProperty=fullName>，不会引发此冲突。 下面的示例演示实现结构 （值类型）<xref:System.Int32.TryParse%2A?displayProperty=fullName>方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1045：不要通过引用来传递类型](../code-quality/ca1045-do-not-pass-types-by-reference.md)