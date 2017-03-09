---
title: "CA1051：不要声明可见实例字段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051：不要声明可见实例字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的类型具有外部可见的实例字段。  
  
## 规则说明  
 字段的主要用途应是作为实现的详细信息。  字段应为 `private` 或 `internal`，并应当通过使用属性来公开。  访问属性和访问字段一样容易，且随着类型的功能扩展，无需引入间断更改即可更改属性的访问器中的代码。  仅返回私有或内部字段值的属性经过优化，可以像访问字段那样执行；在属性上使用外部可见字段不太会提高性能。  
  
 外部可见是指 `public`、`protected` 和 `protected internal`（在 Visual Basic 中为 `Public`、`Protected` 和 `Protected Friend`）可访问性级别。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将字段设置为 `private` 或 `internal`，并使用外部可见属性公开它。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  外部可见字段不提供无法用于属性的任何好处。  另外，不能使用 [链接需求](../Topic/Link%20Demands.md) 保护公共字段。  请参见 [CA2112：受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。  
  
## 示例  
 下面的示例显示了一个违反该规则的类型 \(`BadPublicInstanceFields`\)。  `GoodPublicInstanceFields` 显示更正的代码。  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## 相关规则  
 [CA2112：受保护的类型不应公开字段](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## 请参阅  
 [链接需求](../Topic/Link%20Demands.md)