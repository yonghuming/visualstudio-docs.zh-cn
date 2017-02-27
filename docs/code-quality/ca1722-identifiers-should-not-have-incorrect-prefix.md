---
title: "CA1722：标识符应采用正确的前缀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722：标识符应采用正确的前缀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 标识符的前缀不正确。  
  
## 规则说明  
 按照约定，只有某些编程元素具有以特定前缀开头的名称。  
  
 类型名称没有特定前缀，不应该以“C”作为前缀。  该规则报告诸如“CMyClass”之类的类型名称的冲突，而不会报告诸如“Cache”之类的类型名称的冲突。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 移除标识符的前缀。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1715：标识符应具有正确的前缀](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)