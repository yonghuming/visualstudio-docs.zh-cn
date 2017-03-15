---
title: "关于异常的疑难解答：System.ArgumentException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArgumentException 异常"
  - "System.ArgumentException 异常"
ms.assetid: d8052e62-bc73-4828-87e9-a84ef2a39a5b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ArgumentException
当提供给某个方法的实参中至少有一个不符合该方法的形参规范时，将引发 <xref:System.ArgumentException> 异常。  
  
 在下面的示例中，当发送给方法 `DivideByTwo` 的参数不是偶数时会引发异常。  
  
```vb#  
Module Module1 Sub Main() ' ArgumentException is not thrown in DivideByTwo because 10 is ' an even number. Console.WriteLine("10 divided by 2 is {0}", DivideByTwo(10)) Try ' ArgumentException is thrown in DivideByTwo because 7 is ' not an even number. Console.WriteLine("7 divided by 2 is {0}", DivideByTwo(7)) Catch argEx As ArgumentException ' Tell the user which problem is encountered. Console.WriteLine("7 cannot be evenly divided by 2.") Console.WriteLine("Exception message: " & argEx.Message) End Try ' Uncomment the next statement to see what happens if you call ' DivideByTwo directly. 'Console.WriteLine(DivideByTwo(7)) End Sub Function DivideByTwo(ByVal num As Integer) As Integer ' If num is an odd number, throw an ArgumentException. The ' ArgumentException class provides a number of constructors ' that you can choose from. If num Mod 2 = 1 Then Throw New ArgumentException("Argument for num must be" & _ " an even number.") End If ' Value of num is even, so return half of its value. Return num / 2 End Function End Module  
```  
  
 `ArgumentException` 类的所有实例都应包含用于指定无效的参数以及可接受值的范围的信息。 如果某个更加精确的异常（如 <xref:System.ArgumentNullException> 或 <xref:System.ArgumentOutOfRangeException>）可准确地描述情况，则应使用该异常而不是 `ArgumentException`。  
  
 有关此异常的更多信息（包括其他语言的示例），请参见 <xref:System.ArgumentException>。 有关其他构造函数的列表，请参见 <xref:System.ArgumentException.%23ctor%2A>。  
  
## 请参阅  
 <xref:System.ArgumentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)