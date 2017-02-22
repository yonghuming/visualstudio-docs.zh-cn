---
title: "CA1059：成员不应公开某些具体类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1059：成员不应公开某些具体类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的成员属于某个具体类型，或者它的一个参数或返回值公开某些具体类型。  当前，如果公开了下面的具体类型，该规则会报告出来：  
  
-   由 <xref:System.Xml.XmlNode?displayProperty=fullName> 派生的类型。  
  
## 规则说明  
 具体类型是指具有一个完整实现因此可以实例化的类型。  若要允许广泛使用该成员，应使用建议的接口替换该具体类型。  这样，该成员便可接受实现该接口的任何类型，或在需要实现该接口的类型时能够使用。  
  
 下表列出了目标具体类型及建议的替换接口。  
  
|具体类型|替换|  
|----------|--------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> 使用该接口可将该成员与 XML 数据源的特定实现分离。|  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将具体类型更改为建议的接口。  
  
## 何时禁止显示警告  
 如果需要具体类型提供的特定功能，则可以安全地禁止显示有关此规则的消息。  
  
## 相关规则  
 [CA1011：考虑将基类型作为参数传递](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)