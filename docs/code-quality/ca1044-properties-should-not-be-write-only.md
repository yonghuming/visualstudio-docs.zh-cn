---
title: "CA1044：属性不应是只写的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1044：属性不应是只写的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护属性有 set 访问器，但是没有 get 访问器。  
  
## 规则说明  
 get 访问器提供对属性的读访问，而 set 访问器提供写访问。  虽然可以接受且经常需要使用只读属性，但设计准则禁止使用只写属性。  这是因为允许用户设置值但又禁止该用户查看这个值不能提供任何安全性。  而且，如果没有读访问，将无法查看共享对象的状态，使其用处受到限制。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请向属性添加 get 访问器。  或者，如果需要只写属性的行为，请考虑将此属性转换为方法。  
  
## 何时禁止显示警告  
 强烈建议您不要禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，`BadClassWithWriteOnlyProperty` 是带只写属性的类型。  `GoodClassWithReadWriteProperty` 包含更正的代码。  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]