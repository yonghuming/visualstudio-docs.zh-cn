---
title: "CA1023：索引器不应是多维的 | Microsoft Docs"
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
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1023：索引器不应是多维的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护类型包含一个公共或受保护索引器，该索引器使用多个索引。  
  
## 规则说明  
 索引器（即索引属性）应该使用一个索引。  多维索引器会大大降低库的可用性。  如果设计需要使用多个索引，请重新考虑类型是否代表逻辑数据存储。  否则，请使用方法。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将设计更改为使用长整型或字符串索引，或使用方法来替代索引器。  
  
## 何时禁止显示警告  
 仅在认真考虑非标准索引器的需要后，再禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示类型 `DayOfWeek03`，该类型的多维索引器与该规则冲突。  此索引器可以视为一种转换类型，因此公开为方法更为合适。  此类型在 `RedesignedDayOfWeek03` 中重新设计，以满足该规则。  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## 相关规则  
 [CA1043：将整型或字符串参数用于索引器](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)