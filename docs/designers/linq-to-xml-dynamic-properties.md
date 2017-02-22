---
title: "LINQ to XML 动态属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LINQ to XML 动态属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节提供有关 LINQ to XML 中动态属性的参考信息。具体地说，这些属性由 <xref:System.Xml.Linq> 命名空间中的 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 类公开。  
  
 如[使用 LINQ to XML 的 WPF 数据绑定概述](../designers/wpf-data-binding-with-linq-to-xml-overview.md)主题中所述，每个动态属性都等效于同一类中的标准公共属性或方法。多数情况下应使用这些标准成员；动态属性是专门为 LINQ to XML 数据绑定方案提供的。有关这些类的标准成员的更多信息，请参见 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 参考主题。  
  
 就其解析值而论，本节中的动态属性可分为两类：  
  
-   解析为单个值的简单动态属性，如 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 类中的 `Value` 属性。  
  
-   解析为索引器类型的索引值，如 <xref:System.Xml.Linq.XElement> 的 [Elements](../designers/elements-xelement-dynamic-property.md) 和 [Descendants](../designers/descendants-xelement-dynamic-property.md) 属性。对于要解析为所需值或集合的索引器类型，必须为其传递展开名称参数。  
  
 返回 <xref:System.Collections.Generic.IEnumerable%601> 类型索引值的所有动态属性都使用延迟执行。有关延迟执行的更多信息，请参见 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。  
  
## 本节内容  
  
|主题|说明|  
|--------|--------|  
|[XAttribute 类动态属性](../designers/xattribute-class-dynamic-properties.md)|提供有关由 <xref:System.Xml.Linq.XAttribute> 类公开的动态属性的详细信息。|  
|[XElement 类动态属性](../designers/xelement-class-dynamic-properties.md)|提供有关由 <xref:System.Xml.Linq.XElement> 类公开的动态属性的详细信息。|  
  
## 参考  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## 请参阅  
 [使用 LINQ to XML 的 WPF 数据绑定](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [使用 LINQ to XML 的 WPF 数据绑定概述](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)