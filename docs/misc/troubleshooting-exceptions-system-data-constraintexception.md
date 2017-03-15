---
title: "关于异常的疑难解答：System.Data.ConstraintException | Microsoft Docs"
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
  - "ConstraintException 类"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.ConstraintException
如果尝试进行的操作与约束冲突，则会引发 <xref:System.Data.ConstraintException> 异常。  
  
## 相关提示  
 **放松或关闭数据集内的约束**。  
 在填充 <xref:System.Data.DataSet.EnforceConstraints%2A> 对象中的表时，可使用 <xref:System.Data.DataSet> 属性暂时关闭约束。  
  
 **确保不要尝试在数据表中为已存在主键的主键字段赋值。**  
 如果主键已存在，则会引发此异常。  
  
 **从视图状态加载数据集之前，要先清除数据集。**  
 如果加载时数据集中已有数据，则可能引发此异常。  
  
## 请参阅  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)