---
title: "CA1716：标识符不应与关键字冲突 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1716：标识符不应与关键字冲突
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 某个命名空间、类型或者虚拟成员或接口成员的名称与编程语言中的保留关键字相同。  
  
## 规则说明  
 命名空间、类型以及虚拟和接口成员的标识符不应与针对公共语言运行时的语言所定义的关键字相同。  根据使用的语言和关键字，编译器错误和多义性会导致库难以使用。  
  
 此规则检查下列语言中的关键字：  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 不区分大小写的比较用于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 关键字，区分大小写的比较用于其他语言。  
  
## 如何解决冲突  
 选择一个未在关键字列表中显示的名称。  
  
## 何时禁止显示警告  
 如果您确信该标识符不会让 API 用户感到混淆，而且库在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中的所有可用语言中都可用，则可以禁止显示与该规则有关的警告。