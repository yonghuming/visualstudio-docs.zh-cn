---
title: "CA1009： 正确声明事件处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6191676f94300dfbfafcb8ceb6b0874a8e5b558a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009：正确声明事件处理程序
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 后处理公共或受保护的事件的委托没有正确的签名、 返回类型或参数名称。  
  
## <a name="rule-description"></a>规则说明  
 事件处理程序方法采用两个参数。 第一个委托类型的<xref:System.Object?displayProperty=fullName>和名为发件人。 它是引发事件的对象。 第二个参数属于类型<xref:System.EventArgs?displayProperty=fullName>和名为 e。 这是与该事件关联的数据。 例如，如果打开文件时，将引发事件，事件数据通常包含文件的名称。  
  
 事件处理程序方法不应返回一个值。 在 C# 编程语言中，这指示是返回类型`void`。 事件处理程序可以调用多个对象中的多个方法。 如果允许这些方法以返回一个值，多个返回值将发生的每个事件，而且仅调用的最后一个方法的值将不可用。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更正签名、 返回类型或该委托的参数名称。 有关详细信息，请参阅下面的示例。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例显示一个适合于处理事件的委托。 此事件处理程序可以调用的方法符合设计准则中指定的签名。 `AlarmEventHandler`是委托的类型名称。 `AlarmEventArgs`派生自的事件数据的基类<xref:System.EventArgs>，它包含警报事件数据。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2109：检查可见的事件处理程序](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [处理和引发事件](/dotnet/standard/events/index)  