---
title: "CA2123：重写的链接请求应与基相同 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123：重写的链接请求应与基相同
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 公共类型中的公共或受保护方法重写方法或实现接口，且没有与该接口或虚方法相同的 [链接需求](../Topic/Link%20Demands.md)。  
  
## 规则说明  
 该规则将一个方法与其基方法（该基方法为另一个类型中的接口或虚方法）相匹配，然后比较两者的链接请求。  如果该方法和该基方法中的任何一个具有链接请求，而另一个不具有链接请求，则会报告冲突。  
  
 如果与该规则冲突，则恶意调用方只需调用不安全的方法，即可跳过该链接请求。  
  
## 如何解决冲突  
 若要修复此规则的冲突，请将同一链接请求应用到重写方法或实现。  如果不可能，则使用完全请求标记该方法或完全移除特性。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的各种情况。  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## 请参阅  
 [代码安全维护指南](../Topic/Secure%20Coding%20Guidelines.md)   
 [链接需求](../Topic/Link%20Demands.md)