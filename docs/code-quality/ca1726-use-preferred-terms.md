---
title: "CA1726：使用首选词条 | Microsoft Docs"
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
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726：使用首选词条
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UsePreferredTerms|  
|CheckId|CA1726|  
|类别|Microsoft.Naming|  
|是否重大更改|是 \- 如果对程序集引发<br /><br /> 无间断 \- 如果对类型参数引发|  
  
## 原因  
 在外部可见的标识符的名称中，包括一个存在首选备用词条的词条。  此外，名称中包含“Flag”或“Flags”术语。  
  
## 规则说明  
 此规则将标识符分析为标记。  将对照规则中内置的词条（位于任何自定义字典的“已否决”部分）比较每个单一标记和每个连续的双标记组合。  下表演示该规则中内置的词条以及它们的首选备用词条。  
  
|过时的词条|首选词条|  
|-----------|----------|  
|Arent|AreNot|  
|Cancelled|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag 或 Flags|无替代词条。  不要使用。|  
|Hadnt|HadNot|  
|Hasn’t|HasNot|  
|Havent|HaveNot|  
|Indices|Indexes|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将该词条替换为首选的备用词条。  
  
## 何时禁止显示警告  
 只有当标识符的名称有意且明确地与原始词条（而不是首选词条）相关时，才能禁止显示此规则发出的警告。  
  
## 相关规则  
 [命名警告](../code-quality/naming-warnings.md)