---
title: "CA1504：检查令人误解的字段名 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1504：检查令人误解的字段名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|类别|Microsoft.Maintainability|  
|是否重大更改|非重大更改|  
  
## 原因  
 实例字段的名称以“s\_”开头，或者 `static` （在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Shared`）字段的名称以“m\_”开头。  
  
## 规则说明  
 许多用户将以“s\_”开头的字段名称与静态数据关联。  类似地，以“m\_”开头的字段名称与实例（成员）数据关联。  为了更方便地维护代码，名称应遵循常用的约定。  
  
## 如何解决冲突  
 若要修复与此规则的冲突，请使用相应的前缀重命名字段。  另外，还可以通过添加或移除 `static` 修饰符，使该字段与当前后缀相符。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。