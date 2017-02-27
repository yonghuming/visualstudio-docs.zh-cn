---
title: "CA2212：不要使用 WebMethod 标记服务组件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2212：不要使用 WebMethod 标记服务组件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|类别|Microsoft.Usage|  
|是否重大更改|是|  
  
## 原因  
 某类型中从 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> 继承的方法是使用 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> 标记的。  
  
## 规则说明  
 <xref:System.Web.Services.WebMethodAttribute> 适用于在 XML Web 服务内使用 ASP.NET 创建的方法；它使方法能从远程 Web 客户端被调用。  方法和类必须是公共的，并且必须在 ASP.NET Web 应用程序中执行。  <xref:System.EnterpriseServices.ServicedComponent> 类型由 COM\+ 应用程序承载，可以使用 COM\+ 服务。  <xref:System.Web.Services.WebMethodAttribute> 不会应用于 <xref:System.EnterpriseServices.ServicedComponent> 类型，，因为它们不是供相同情况使用的。  具体地说，将该特性添加到 <xref:System.EnterpriseServices.ServicedComponent> 方法不会使该方法可以从远程 Web 客户端被调用。  因为 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.EnterpriseServices.ServicedComponent> 方法在上下文和事务流方面的行为和要求有冲突，所以该方法的行为在某些情况下会不正确。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请从 <xref:System.EnterpriseServices.ServicedComponent> 方法中移除该特性。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  在任何情况下将这些元素组合在一起都是不正确的。  
  
## 请参阅  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>