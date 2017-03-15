---
title: "CA2108：检查有关值类型的声明性安全 | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108：检查有关值类型的声明性安全
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|类别|Microsoft.Security|  
|是否重大更改|否|  
  
## 原因  
 公共或受保护值类型受 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) 或 [链接需求](../Topic/Link%20Demands.md) 保护。  
  
## 规则说明  
 在其他构造函数执行之前，值类型的默认构造函数会分配并初始化值类型。  如果值类型受到 Demand 或 LinkDemand 的保护，并且调用方不具有能够通过安全检查的权限，则默认构造函数以外的任何构造函数将失败，并且将引发安全异常。  值类型不会被释放；它保持由其默认构造函数设置的状态。  不要假定传递值类型的实例的调用方具有创建或访问该实例的权限。  
  
## 如何解决冲突  
 除非从类型中移除安全检查，并且使用方法级别的安全检查作为替代，否则无法修复与该规则有关的冲突。  注意，以这种方式修复冲突并不会阻止权限不足的调用方获取值类型的实例。  必须确保默认状态下的值类型的实例不会公开敏感信息，并且不能以有害方式使用该实例。  
  
## 何时禁止显示警告  
 如果任何调用方可以获取默认状态下的值类型的实例，而不会造成安全风险，则可以禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的包含值类型的库。  注意，`StructureManager` 类型假定传递值类型的实例的调用方具有创建或访问该实例的权限。  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## 示例  
 下面的应用程序演示库的漏洞。  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 该示例产生下面的输出。  
  
  **Structure custom constructor: Request failed.**  
**New values SecuredTypeStructure 100 100**  
**New values SecuredTypeStructure 200 200**   
## 请参阅  
 [链接需求](../Topic/Link%20Demands.md)   
 [数据和建模](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)