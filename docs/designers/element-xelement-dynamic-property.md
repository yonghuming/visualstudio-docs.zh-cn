---
title: "元素（XElement 动态属性） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 元素（XElement 动态属性）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

获取一个索引器，用于检索与指定扩展名对应的子元素实例。  
  
## 语法  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## 属性值\/返回值  
 一个类型为 `XElement Item(String expandedName)` 的索引器。此索引器获取扩展名参数并返回相应的 <xref:System.Xml.Linq.XElement>，或者如果没有具有指定名称的元素，则返回 `null`。  
  
## 备注  
 此属性等效于 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 类的 <xref:System.Xml.Linq.XContainer.Element%2A> 方法。  
  
## 请参阅  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement 类动态属性](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)