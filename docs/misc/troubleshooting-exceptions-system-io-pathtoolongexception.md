---
title: "关于异常的疑难解答：System.IO.PathTooLongException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "PathTooLongException 类"
ms.assetid: 8912c425-bf91-42e3-82d8-bee6b2062db3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IO.PathTooLongException
当路径名或文件名长度超过系统定义的最大长度时引发 <xref:System.IO.PathTooLongException> 异常。  
  
## 相关提示  
 **确保路径的长度不大于系统定义的最大长度。**  
 在基于 Windows 的平台上，路径必须少于 248 个字符，文件名必须少于 260 个字符。  
  
## 请参阅  
 <xref:System.IO.PathTooLongException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：分析文件路径](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)