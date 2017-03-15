---
title: "CA1719：参数名不应与成员名冲突 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1719：参数名不应与成员名冲突
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 在不区分大小写的比较中，外部可见的成员的名称匹配其某个参数的名称。  
  
## 规则说明  
 参数名称应传达参数的含义，成员名称应传达成员的含义。  两者相同的设计非常少见。  使参数与其成员同名会导致不直观的效果，会使库难以使用。  
  
## 如何解决冲突  
 选择不匹配成员名称的参数名称。  
  
## 何时禁止显示警告  
 对于新的开发，在已知情况中尚未发现必须禁止显示此规则发出的警告的情况。  如果要发布库，则可能必须禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：标识符不应包含下划线](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)