---
title: "CA1408：请不要使用 AutoDual ClassInterfaceType | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408：请不要使用 AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 通过将 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性设置为 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `AutoDual` 值来标记组件对象模型 \(COM\) 可见的类型。  
  
## 规则说明  
 使用双重接口的类型使客户端可以绑定到特定的接口布局。  如果在将来的版本中对该类型或任何基类型的布局进行更改，将中断绑定到该接口的 COM 客户端。  默认情况下，如果未指定 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 特性，将使用仅支持调度的接口。  
  
 除非另行标记，否则所有公共的非泛型类型都对 COM 可见；所有非公共类型和泛型类型都对 COM 不可见。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 特性的值更改为 <xref:System.Runtime.InteropServices.ClassInterfaceType> 的 `None` 值并显式定义该接口。  
  
## 何时禁止显示警告  
 除非可以肯定该类型及其基类型的布局不会在将来的版本中更改，否则不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类以及为使用显式接口而对该类的重新声明。  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## 相关规则  
 [CA1403：自动布局类型不应对 COM 可见](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412：将 ComSource 接口标记为 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## 请参阅  
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-cn/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [为互操作限定 .NET 类型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)