---
title: "关于异常的疑难解答：System.MissingFieldException | Microsoft Docs"
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
  - "MissingFieldException 类"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.MissingFieldException
尝试动态访问不存在的字段时，会引发 <xref:System.MissingFieldException> 异常。  
  
## 相关提示  
 **如果类库中的某个字段已被移除或重命名，请重新编译引用该库的所有程序集。**  
 此异常在尝试动态访问未通过其强名称引用的程序集中已删除或重命名的字段时生成。  
  
## 请参阅  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)