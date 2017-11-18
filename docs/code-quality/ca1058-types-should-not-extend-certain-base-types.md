---
title: "CA1058： 类型不应扩展某些基类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45cddd908c53d129a230b998c6dad03196a31c49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058：类型不应扩展某些基类型
|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见的类型扩展某些基类型。 目前，此规则将报告以下类型派生的类型：  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## <a name="rule-description"></a>规则说明  
 有关[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]版本 1，它建议派生新异常从<xref:System.ApplicationException>。 此建议已更改和新的异常应派生自<xref:System.Exception?displayProperty=fullName>或在其子类之一<xref:System>命名空间。  
  
 不创建的一个子类<xref:System.Xml.XmlDocument>如果你想要创建基础的对象模型或数据源的 XML 视图。  
  
### <a name="non-generic-collections"></a>非泛型集合  
 使用和/或延长尽可能的泛型集合。 除非以前传送不会扩展在代码中，有非泛型集合。  
  
 **不正确的用法的示例**  
  
```csharp  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **正确用法示例**  
  
```csharp  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请从不同的基类型或泛型集合派生类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止有关显示此规则，冲突的警告<xref:System.ApplicationException>。 则可以安全地禁止违反此规则的警告显示有关<xref:System.Xml.XmlDocument>。 则可以安全地禁止显示警告有关非泛型集合，如果以前发布的代码。