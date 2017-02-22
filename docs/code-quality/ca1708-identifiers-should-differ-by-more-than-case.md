---
title: "CA1708：标识符不应仅以大小写进行区分 | Microsoft Docs"
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
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1708：标识符不应仅以大小写进行区分
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 转换为小写形式后，两个类型、成员、参数或完全限定命名空间的名称相同。  
  
## 规则说明  
 不能仅通过大小写区分命名空间、类型、成员和参数的标识符，因为针对公共语言运行时的语言不需要区分大小写。  例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 是广泛使用的不区分大小写的语言。  
  
 此规则仅在公共可见成员上激发。  
  
## 如何解决冲突  
 选择一个唯一的名称（与其他标识符进行不区分大小写的比较）。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 中，库可能并非在所有可用语言中都可以使用。  
  
## 冲突的示例  
 下面的示例演示与此规则的冲突。  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## 相关规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)