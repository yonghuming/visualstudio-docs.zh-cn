---
title: "CA1725：参数名应与基方法中的声明保持一致 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1725：参数名应与基方法中的声明保持一致
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 外部可见的方法重写中的参数名与该方法的基声明中的参数名或者与该方法的接口声明中的参数名不一致。  
  
## 规则说明  
 以一致的方式命名重写层次结构中的参数可以提高方法重写的可用性。  如果派生方法中的参数名与基声明中的名称不同，可能会导致无法区分出该方法是基方法的重写还是该方法的新重载。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请重命名该参数，使其与基声明中的参数名一致。  此修复是对 COM 可见方法的重大更改。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告，但对以前发布的库中的 COM 可见方法除外。