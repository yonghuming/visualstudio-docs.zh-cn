---
title: "关于异常的疑难解答：System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException 类"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Runtime.InteropServices.SafeArrayRankMismatchException
如果传入的 SAFEARRAY 的秩与托管签名中指定的秩不匹配，则会引发 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> 异常。  
  
## 相关提示  
 **确保您的数组具有所需的维数。**  
 由于安全数组的秩和界限不能根据类型库确定，因此假定秩等于 1，而假定下限等于 0。 秩和界限必须在由[Tlbimp.exe（类型库导入程序）](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 产生的托管签名中定义。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [数组的默认封送处理](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [数组](/dotnet/visual-basic/programming-guide/language-features/arrays/index)