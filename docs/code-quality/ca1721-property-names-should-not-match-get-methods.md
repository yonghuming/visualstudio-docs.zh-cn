---
title: "CA1721：属性名不应与 get 方法冲突 | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721：属性名不应与 get 方法冲突
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护成员的名称以“Get”开头，且其余部分与公共或受保护属性的名称匹配。  例如，包含名为“GetColor”的方法和名为“Color”的属性的类型与该规则冲突。  
  
## 规则说明  
 Get 方法和属性的名称应当能够明确表示其功能。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这缩短了学习新软件库所需的时间，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 更改该名称，使其不与前缀为“Get”的方法名称匹配。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
> [!NOTE]
>  如果 Get 方法是由实现 IExtenderProvider 接口引起的，则可以排除此警告。  
  
## 示例  
 下面的示例包含与该规则冲突的方法和属性。  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## 相关规则  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)