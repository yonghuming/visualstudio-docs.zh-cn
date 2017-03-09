---
title: "关于异常的疑难解答：System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "InvalidCastException 类"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.InvalidCastException
当在显式引用转换期间发生失败时，会引发 <xref:System.InvalidCastException> 异常。 引用转换是从一种引用类型到另一种引用类型的转换。 引用转换可以更改引用的类型，但从不更改转换目标的类型或值。 将对象从一种类型强制转换为另一种类型是此异常的常见原因。  
  
## 相关提示  
 **核对源类型和目标类型以确保转换有效。**  
 有关系统所支持的转换的信息，请参见 <xref:System.Convert>。  
  
## 备注  
 为了使显式引用转换成功，源值必须为 Null（在 Visual Basic 中为 `Nothing`），或者源参数引用的对象类型必须可通过隐式引用转换转换为目标类型。  
  
 当调用用户控件中的自定义事件的 Visual Basic 6.0 应用程序升级为较新版本的 Visual Basic 并运行时，可能发生此异常，并带有额外的信息“指定的转换无效”。 若要解决此错误，请在 `Form1` 中查找下面的代码行：  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 并将其替换为：  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## 请参阅  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：在 Visual Basic 中将一个对象转换为其他类型](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [将字符串转换为 .NET Framework 数据类型](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [如何：在结构之间实现用户定义的转换](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)