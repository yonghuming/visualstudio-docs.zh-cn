---
title: "关于异常的疑难解答：System.IndexOutOfRangeException | Microsoft Docs"
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
  - "IndexOutOfRangeException 类"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IndexOutOfRangeException
当尝试使用一个超出数组界限或小于零的索引访问数组或集合的元素时，会引发 <xref:System.IndexOutOfRangeException> 异常。  
  
## 相关提示  
 **确保列表中的最大索引小于列表的大小**  
 列表中的最大索引必须小于列表的大小。  
  
 **确保索引不是负数。**  
 如果索引小于零，将引发此异常。  
  
 **确保数据列名称正确。**  
 如果提供给 <xref:System.Data.DataView.Sort%2A?displayProperty=fullName> 属性的数据列名称无效，则可能引发此异常。 有关更多信息，请参见 <xref:System.Data.DataView> 类。  
  
## 示例  
  
### 描述  
 下面的示例在索引 `Try…Catch` 超出数组界限（0 到 3）时使用 `IndexOutOfRangeException` 块捕获 `i`。 示例显示下面的内容：  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### 代码  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## 请参阅  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [数组](/dotnet/visual-basic/programming-guide/language-features/arrays/index)