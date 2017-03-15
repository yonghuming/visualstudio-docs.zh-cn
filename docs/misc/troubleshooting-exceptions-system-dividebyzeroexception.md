---
title: "关于异常的疑难解答：System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "DivideByZeroException 类"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.DivideByZeroException
当尝试将整数或小数值除以零时，会引发 <xref:System.DivideByZeroException> 异常。  
  
## 相关提示  
 **在执行除法运算之前，请确保分母的值不为零。**  
 根据 IEEE 算法的规则，将浮点值除以零会产生正无穷、负无穷或“不是数字”\(NaN\)。 浮点运算永远不会引发异常。  
  
## 请参阅  
 <xref:System.DivideByZeroException>   
 [算术运算符 \(Visual Basic\)](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)