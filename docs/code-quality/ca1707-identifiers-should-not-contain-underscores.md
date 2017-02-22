---
title: "CA1707：标识符不应包含下划线 | Microsoft Docs"
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
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707：标识符不应包含下划线
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|类别|Microsoft.Naming|  
|是否重大更改|间断 \- 如果对程序集引发<br /><br /> 无间断 \- 如果对类型参数引发|  
  
## 原因  
 标识符的名称包含下划线 \(\_\) 字符。  
  
## 规则说明  
 按照约定，标识符名称不包含下划线 \(\_\) 字符。  该规则将检查命名空间、类型、成员和参数。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 从名称中移除所有下划线字符。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)