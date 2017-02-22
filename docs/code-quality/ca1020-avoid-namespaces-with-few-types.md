---
title: "CA1020：避免使用类型极少的命名空间 | Microsoft Docs"
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
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1020：避免使用类型极少的命名空间
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 全局命名空间以外的某命名空间包含的类型少于五个。  
  
## 规则说明  
 请确保每个命名空间都有一个逻辑组织，并确保将类型放入稀疏填充的命名空间是存在有效理由的。  命名空间应包含在大多数情况下要一起使用的类型。  当类型的应用程序互斥时，这些类型应位于不同的命名空间中。  例如，<xref:System.Web.UI> 命名空间包含在 Web 应用程序中使用的类型，<xref:System.Windows.Forms> 命名空间包含在基于 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 的应用程序中使用的类型。  即使两个命名空间具有控制用户界面的类型，这些类型没有设计用于同一应用程序。  因此，它们在单独的命名空间中。  谨慎组织命名空间也会有所帮助，因为这样可以增强功能的发现能力。  通过检查命名空间层次结构，库使用者应能够定位实现功能的类型。  
  
> [!NOTE]
>  要符合此原则，设计时类型和权限应不合并到其他命名空间中。  这些类型位于主命名空间下自己的命名空间中，而且这些命名空间应分别以 `.Design` 和 `.Permissions` 结束。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请尝试将包含少量类型的命名空间合并到一个命名空间中。  
  
## 何时禁止显示警告  
 在命名空间不包含与其他命名空间中的类型一起使用的类型时，可以安全地禁止显示此规则发出的警告。