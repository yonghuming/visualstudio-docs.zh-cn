---
title: "关于异常的疑难解答：System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolicyValidationException 异常"
  - "System.IdentityModel.Selectors.PolicyValidationException 异常"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IdentityModel.Selectors.PolicyValidationException
当无法对接收方提供的策略进行验证时，将引发 <xref:System.IdentityModel.Selectors.PolicyValidationException> 异常。 有关策略要求的详细信息，请参阅 [Information Card Profile V1.0 技术参考](http://go.microsoft.com/fwlink/?LinkID=102401)。  
  
 任何无效的策略内容都会导致此失败。 有关策略内容的常见问题包括：  
  
-   无效的键类型  
  
-   无效的键大小  
  
-   无效的 XML  
  
-   策略中未指定任何声明（必须至少指定一个非可选声明）  
  
## 请参阅  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)