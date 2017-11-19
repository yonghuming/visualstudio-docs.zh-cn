---
title: "CA1711： 标识符不应具有正确的后缀 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e0701c93146b4cc460a7216d2f4159832389db6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711：标识符应采用正确的后缀
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 标识符具有不正确的后缀。  
  
## <a name="rule-description"></a>规则说明  
 按照约定，只有扩展某些基类型或实现某些接口或从这些类型派生的类型的类型的名称应该以特定的保留后缀结尾。 其他类型名称不应使用这些保留的后缀。  
  
 下表列出了保留的后缀的基类型和是对与其关联的接口。  
  
|后缀|基类型/接口|  
|------------|--------------------------|  
|特性|<xref:System.Attribute?displayProperty=fullName>|  
|集合|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|词典|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|事件处理程序|一个事件处理程序委托|  
|例外|<xref:System.Exception?displayProperty=fullName>|  
|权限|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|堆栈|<xref:System.Collections.Stack?displayProperty=fullName>|  
|流|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 此外，以下后缀应**不**使用：  
  
-   委托  
  
-   Enum  
  
-   以 Impl-改为使用的 Core  
  
-   Ex 或类似的后缀，以便进行区分相同类型的早期版本  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 类型名中删除后缀。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 除非后缀在应用程序域中具有明确的含义，否则不要禁止显示来自此规则的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1710：标识符应具有正确的后缀](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## <a name="see-also"></a>另请参阅  
 [特性](/dotnet/standard/design-guidelines/attributes)   
 [处理和引发事件](/dotnet/standard/events/index)  