---
title: "关于异常的疑难解答：System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException 类"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Security.VerificationException
当安全策略要求代码是类型安全的，而验证过程无法验证该代码是否类型安全时，就会引发 <xref:System.Security.VerificationException> 异常。  
  
## 相关提示  
 确保应用程序所加载的类库的两个版本不冲突。  
 作为验证过程的一部分，系统会检查 MSIL（Microsoft 中间语言）的类型安全性，以确保对象安全地相互隔离，并因而免于意外损坏或恶意损坏。 有关详细信息，请参阅[类型安全和安全性](http://msdn.microsoft.com/zh-cn/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)。  
  
## 请参阅  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)