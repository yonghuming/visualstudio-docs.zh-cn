---
title: "CA2112： 受保护的类型不应公开字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d60784b92d414b6a226605cd406378c1686529dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112：受保护的类型不应公开字段
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型包含公共字段，并受[链接需求](/dotnet/framework/misc/link-demands)。  
  
## <a name="rule-description"></a>规则说明  
 如果代码可以访问受链接要求保护的类型的实例，则该代码不必满足此链接要求就可以访问该类型的字段。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使非公共字段，并添加公共属性或方法返回的字段数据。 类型的 LinkDemand 安全检查保护对该类型的属性和方法的访问。 但是，代码访问安全性不适用于字段。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 安全问题并获得良好的设计，你应通过进行公共字段 nonpublic 解决冲突。 如果该字段不保留应保持安全的信息，你可以禁止显示此规则的警告和不要依赖于字段的内容。  
  
## <a name="example"></a>示例  
 下面的示例组成库类型 (`SecuredTypeWithFields`) 使用不安全的字段，类型 (`Distributor`)，可以创建库的类型的实例并有错误的传递到类型的实例没有权限来创建它们，和应用程序代码可以读取一个实例的字段，即使它没有保护的类型的权限。  
  
 下面的库代码违反了规则。  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>示例  
 由于用于保护受保护的类型的链接要求，应用程序无法创建实例。 下面的类使应用程序以获取受保护的类型的实例。  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>示例  
 以下应用程序演示了如何操作，如果没有权限才能访问受保护的类型的方法，代码可以访问其字段。  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 本示例生成以下输出。  
  
 **创建 SecuredTypeWithFields 的实例。**  
**受保护类型字段： 22、 33**  
**更改受保护的类型的字段...**  
**缓存对象字段： 99，33**   
## <a name="related-rules"></a>相关的规则  
 [CA1051：不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>另请参阅  
 [链接需求](/dotnet/framework/misc/link-demands)   
 [数据和建模](/dotnet/framework/data/index)