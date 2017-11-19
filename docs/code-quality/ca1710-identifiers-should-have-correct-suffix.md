---
title: "CA1710： 标识符应具有正确的后缀 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fd4f23ab77e2b810d5064bd45e9f7d530e9844e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710：标识符应具有正确的后缀
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|CheckId|CA1710|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 标识符没有正确的后缀。  
  
## <a name="rule-description"></a>规则说明  
 按照约定，扩展某些基类型或实现某些接口或从这些类型派生的类型的类型的名称具有与基类型或接口关联的后缀。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
 下表列出的基类型和具有关联的后缀的接口。  
  
|基类型/接口|后缀|  
|--------------------------|------------|  
|<xref:System.Attribute?displayProperty=fullName>|特性|  
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|  
|<xref:System.Exception?displayProperty=fullName>|例外|  
|<xref:System.Collections.ICollection?displayProperty=fullName>|集合|  
|<xref:System.Collections.IDictionary?displayProperty=fullName>|词典|  
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|集合|  
|<xref:System.Collections.Queue?displayProperty=fullName>|集合或队列|  
|<xref:System.Collections.Stack?displayProperty=fullName>|集合或堆栈|  
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|集合|  
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|词典|  
|<xref:System.Data.DataSet?displayProperty=fullName>|数据集|  
|<xref:System.Data.DataTable?displayProperty=fullName>|集合或 DataTable|  
|<xref:System.IO.Stream?displayProperty=fullName>|流|  
|<xref:System.Security.IPermission?displayProperty=fullName>|权限|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|条件|  
|一个事件处理程序委托。|事件处理程序|  
  
 类型实现<xref:System.Collections.ICollection>和是一种通用的类型的数据结构，如字典、 堆栈或队列，允许将提供有意义的预期用法的信息类型的名称。  
  
 类型实现<xref:System.Collections.ICollection>和特定项的集合对具有以单词 Collection 结尾的名称。 例如，集合<xref:System.Collections.Queue>对象将具有名称 QueueCollection。 Collection 后缀表示集合的成员，可以通过使用枚举`foreach`(`For Each`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 语句。  
  
 类型实现<xref:System.Collections.IDictionary>具有名称以单词 '词典' 结尾，即使该类型还实现<xref:System.Collections.IEnumerable>或<xref:System.Collections.ICollection>。 Collection 和字典后缀命名约定使用户能够区分以下两个枚举模式。  
  
 Collection 后缀的类型遵循此枚举模式。  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 具有 '词典' 后缀类型遵循此枚举模式。  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 A<xref:System.Data.DataSet>对象的集合组成<xref:System.Data.DataTable>包含的集合的对象<xref:System.Data.DataColumn?displayProperty=fullName>和<xref:System.Data.DataRow?displayProperty=fullName>对象以及其他。 这些集合实现<xref:System.Collections.ICollection>通过基<xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>类。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 重命名类型，以便为正确的术语作为后缀。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示警告，以使用 Collection 后缀，如果类型是一种通用的数据结构可能会扩展，或将包含任意一组不同的项。 在这种情况下，提供有关实现、 性能或数据结构的其他特征有意义的信息的名称 binarytree (例如，)。 在其中类型表示特定类型 (例如，StringCollection) 的集合的情况下，不要禁止显示此规则的警告由于后缀表示后，可以使用枚举类型`foreach`语句。  
  
 对于其他后缀，不要禁止显示此规则的警告。 该后缀，可为可见的类型名中的预期的用法。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1711：标识符应采用正确的后缀](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## <a name="see-also"></a>另请参阅  
 [特性](/dotnet/standard/design-guidelines/attributes)   
 [处理和引发事件](/dotnet/standard/events/index)  