---
title: "特性（XElement 动态属性） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 特性（XElement 动态属性）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

获取一个索引器，该索引器用于检索与指定扩展名对应的属性实例。  
  
## 语法  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## 属性值\/返回值  
 一个类型为 `XAttribute Item(String expandedName)` 的索引器。此索引器获取指定属性的扩展名，然后返回相应的 <xref:System.Xml.Linq.XAttribute>，如果没有具有指定名称的属性，则返回 `null`。  
  
## 备注  
 此属性等效于 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 类的 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法。  
  
## 请参阅  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement 类动态属性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xattribute-dynamic-property.md)