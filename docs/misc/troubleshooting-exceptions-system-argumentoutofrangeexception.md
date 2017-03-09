---
title: "关于异常的疑难解答：System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "ArgumentOutOfRangeException 类"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ArgumentOutOfRangeException
当调用某个方法，并且传递给该方法的参数中至少有一个参数不是空引用（Visual Basic 中是 <xref:System.ArgumentOutOfRangeException>）且不包含有效值时，就会引发 `Nothing`。  
  
## 相关提示  
 **请确保传给此方法的所有参数都有被调用的方法所定义的有效值。**  
 不是空引用的参数必须包含有效值。  
  
 **如果您正在处理集合，请确保索引小于集合的大小。**  
 索引必须在集合的大小范围之内，不能超过该大小范围或小于零。 有关更多信息，请参见[集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 **当使用 ComboBox 或 ListBox 类的重载的双参数 FindString 或 FindStringExact 方法时，请检查 startIndex 参数**。  
 如果 `startIndex` 等于相关列表的最后一项的索引值，则可能引发此异常。 若要解决此问题，请将 0 作为 `startIndex` 参数传入，或使用单参数的 `FindString` 或 `FindStringExact` 方法。 有关详细信息，请参阅[CComboBox::FindString](../Topic/CComboBox::FindString.md)或[CListBox::FindString](../Topic/CListBox::FindString.md)。  
  
## 请参阅  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)