---
title: "关于异常的疑难解答：System.FieldAccessException | Microsoft Docs"
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
  - "FieldAccessException 类"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.FieldAccessException
无效地尝试访问类中的私有或受保护字段时，将引发 <xref:System.FieldAccessException> 异常。  
  
## 相关提示  
 **如果类库中某个字段的访问级别已经改变，请重新编译引用该库的所有程序集。**  
 当类库中字段的访问级别（`Public`，`Private` 等）被更改，而一个或多个引用此库的程序集未重新编译时，就会引发此异常。  
  
## 请参阅  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)