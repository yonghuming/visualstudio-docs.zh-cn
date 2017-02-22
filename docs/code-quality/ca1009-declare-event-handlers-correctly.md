---
title: "CA1009：正确声明事件处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1009：正确声明事件处理程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 处理公共事件或受保护事件的某委托没有正确的签名、返回类型或参数名称。  
  
## 规则说明  
 事件处理程序方法采用两个参数。  第一个参数是 <xref:System.Object?displayProperty=fullName> 类型，名为“sender”。  它是引发事件的对象。  第二个参数是 <xref:System.EventArgs?displayProperty=fullName> 类型，名为“e”。  这是与该事件关联的数据。  例如，如果在每次打开文件时都引发事件，则事件数据通常包含文件名称。  
  
 事件处理程序方法不应返回值。  在 C\# 编程语言中，这是由 `void` 返回类型指示的。  一个事件处理程序可以调用多个对象中的多个方法。  如果允许这些方法返回值，则每个事件都将发生多个返回值，并且只有调用的最后一个方法的值可用。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请更正该委托的签名、返回类型或参数名称。  有关详细信息，请参见下面的示例。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示适合处理事件的委托。  可通过此事件处理程序调用的方法符合设计指南中指定的签名。  `AlarmEventHandler` 是委托的类型名称。  `AlarmEventArgs` 派生自事件数据的基类 <xref:System.EventArgs>，它包含警报事件数据。  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## 相关规则  
 [CA2109：检查可见的事件处理程序](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## 请参阅  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [事件和委托](http://msdn.microsoft.com/zh-cn/d98fd58b-fa4f-4598-8378-addf4355a115)