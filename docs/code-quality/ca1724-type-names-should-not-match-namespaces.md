---
title: "CA1724：类型名不应与命名空间冲突 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1724：类型名不应与命名空间冲突
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 在不区分大小写的比较中，类型名称与 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 命名空间名称匹配。  
  
## 规则说明  
 类型名称不应该与 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库中定义的命名空间的名称匹配。  与该规则冲突将使库的可用性下降。  
  
## 如何解决冲突  
 选择与 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库命名空间的名称不匹配的类型名。  
  
## 何时禁止显示警告  
 对于新的开发，在已知情况中尚未发现必须禁止显示此规则发出的警告的情况。  在禁止显示此警告之前，请仔细考虑匹配的名称可能会怎样让库的用户感到混淆。  如果要发布库，则可能必须禁止显示此规则发出的警告。