---
title: "CA1065： 不要引发意外的位置中的异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3511778536bb9664726fc9a61b4773c209a0fd46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065：不要在意外的位置引发异常
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 不应引发异常的方法引发了异常。  
  
## <a name="rule-description"></a>规则说明  
 不应引发异常的方法可以进行分类，如下所示：  
  
-   属性 Get 方法  
  
-   事件访问器方法  
  
-   Equals 方法  
  
-   GetHashCode 方法  
  
-   ToString 方法  
  
-   静态构造函数  
  
-   终结器  
  
-   Dispose 方法  
  
-   相等运算符  
  
-   隐式强制转换运算符  
  
 以下各节讨论这些方法类型。  
  
### <a name="property-get-methods"></a>属性 Get 方法  
 属性是基本上就是智能字段。 因此，它们应该表现得像尽可能多的字段。 字段不会引发异常，也不应该这样属性。 如果你有一个属性，将引发异常，请考虑使它成为方法。  
  
 允许从属性的 get 方法引发以下例外：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>和所有衍生产品 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>和所有派生对象  
  
-   <xref:System.ArgumentException?displayProperty=fullName>（仅从索引，以获得）  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>（仅从索引，以获得）  
  
### <a name="event-accessor-methods"></a>事件访问器方法  
 事件访问器应不会引发异常的简单操作。 当你尝试添加或删除事件处理程序时，事件不应引发异常。  
  
 允许从事件访问器中引发以下例外：  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>和所有衍生产品 (包括<xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>和所有派生对象  
  
-   <xref:System.ArgumentException>和派生产品  
  
### <a name="equals-methods"></a>Equals 方法  
 以下**等于**方法不应引发异常：  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **等于**方法应返回`true`或`false`而不是引发异常。 例如，如果向 Equals 传递两个不匹配的类型它应只返回`false`而不是引发<xref:System.ArgumentException>。  
  
### <a name="gethashcode-methods"></a>GetHashCode 方法  
 以下**GetHashCode**方法应通常不引发异常：  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode**应始终会返回值。 否则，可能会丢失哈希表中的项。  
  
 版本**GetHashCode**采用自变量可以引发<xref:System.ArgumentException>。 但是， **Object.GetHashCode**应永远不会引发异常。  
  
### <a name="tostring-methods"></a>ToString 方法  
 调试器使用<xref:System.Object.ToString%2A?displayProperty=fullName>有助于字符串格式显示有关对象的信息。 因此， **ToString**不能更改对象的状态，并且不应引发异常。  
  
### <a name="static-constructors"></a>静态构造函数  
 从静态构造函数引发的异常会导致无法使用当前的应用程序域中的类型。 你应为引发静态构造函数从异常中提供非常充分的理由 （例如安全问题）。  
  
### <a name="finalizers"></a>终结器  
 来自终结器引发异常会导致 CLR 很快失败，其关闭进程。 因此，在终结器引发的异常应始终避免。  
  
### <a name="dispose-methods"></a>Dispose 方法  
 A<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法不应引发异常。 释放情况通常称作清理中逻辑的一部分`finally`子句。 因此，显式释放从引发异常强制用户添加异常处理内部`finally`子句。  
  
 **Dispose(false)**代码路径应永远不会引发异常，因为这几乎始终从调用的终结器。  
  
### <a name="equality-operators--"></a>相等运算符 (= =、 ！ =)  
 等于像方法一样，相等运算符应返回`true`或`false`和不应引发异常。  
  
### <a name="implicit-cast-operators"></a>隐式强制转换运算符  
 因为用户通常不知道已调用隐式强制转换运算符，通过隐式强制转换运算符引发的异常是完全意外。 因此，应从隐式强制转换运算符不引发任何异常。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 对于属性 getter，或者更改逻辑，以便它不再具有引发异常，或将属性更改为一种方法。  
  
 对于所有其他方法类型前面列出的更改逻辑，以便它不再必须引发异常。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果冲突引起的异常声明而不是引发的异常。  
  
## <a name="related-rules"></a>相关的规则  
 [CA2219：在异常子句中不引发异常](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## <a name="see-also"></a>另请参阅  
 [设计警告](../code-quality/design-warnings.md)