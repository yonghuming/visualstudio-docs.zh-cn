---
title: "关于异常的疑难解答：System.OverflowException | Microsoft Docs"
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
  - "OverflowException 类"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.OverflowException
在检查的上下文中执行的算术、强制转换或转换运算导致溢出时，会引发 <xref:System.OverflowException> 异常。 当运算生成的值对于目标类型来说太大、无穷或“不是数字”\(NaN\) 时，会发生溢出。  
  
## 相关提示  
 **当从一个数字执行强制转换时，值必须是一个小于无限大的有效数字。**  
 源值不能为无穷或“不是数字”。  
  
 **确保不会被零除。**  
 除零时通常会产生此异常。  
  
## 备注  
 在检测溢出的语言中，<xref:System.OverflowException> 异常在发生溢出时引发。 例如，在 C\# 中，`checked` 关键字用来检测溢出条件。<xref:System.OverflowException> 异常仅发生在所检查的上下文中。  
  
 对于从超出目标类型范围的整型或小数类型算术运算或转换中得出的结果：  
  
-   在所检查的上下文中，如果该运算是常数表达式，则发生编译时错误。 否则，如果该运算在运行时执行，则引发 <xref:System.OverflowException> 异常。  
  
-   在未选中的上下文中将结果截断，方法是：丢弃任何不适应目标类型的高序位。  
  
 有关数据类型的值范围的信息，请参阅[数据类型](/dotnet/visual-basic/language-reference/data-types/data-type-summary)、[整型表](/dotnet/csharp/language-reference/keywords/integral-types-table)或[浮点型表](/dotnet/csharp/language-reference/keywords/floating-point-types-table)。  
  
## 请参阅  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)