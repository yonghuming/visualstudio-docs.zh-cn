---
title: "关于异常的疑难解答：System.MethodAccessException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "MethodAccessException 类"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.MethodAccessException
无效地尝试访问类中私有或受保护的方法时，将引发 <xref:System.MethodAccessException> 异常。  
  
## 相关提示  
 **如果类库中某方法的访问级别已经改变，请重新编译引用该库的所有程序集。**  
 此异常通常在调用方不具有对成员的访问权限时发生。  
  
## 请参阅  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)