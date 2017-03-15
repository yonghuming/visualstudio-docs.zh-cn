---
title: "托管代码的“托管最少量规则”规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 2
---
# 托管代码的“托管最少量规则”规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

The Managed Minimum Rules focus on the most critical problems in your code, including potential security holes, application crashes, and other important logic and design errors.  您应在为项目创建的任何自定义规则集中包含此规则集。  
  
|规则|说明|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Types that own disposable fields should be disposable|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Remove empty finalizers|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|应释放可释放的字段|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Overload operator equals on overriding ValueType.Equals|