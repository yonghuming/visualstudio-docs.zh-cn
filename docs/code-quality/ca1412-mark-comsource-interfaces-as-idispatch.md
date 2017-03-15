---
title: "CA1412：将 ComSource 接口标记为 IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412：将 ComSource 接口标记为 IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 有一个类型用 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 特性进行了标记，并且至少有一个指定的接口未用设置为 `InterfaceIsDispatch` 值的 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 特性进行标记。  
  
## 规则说明  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 用于标识类向组件对象模型 \(COM\) 客户端公开的事件接口。  这些接口必须公开为 `InterfaceIsIDispatch`，以便允许 Visual Basic 6 COM 客户端接收事件通知。  默认情况下，如果接口未用 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 特性进行标记，则它将公开为双重接口。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请针对指定了 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 特性的所有接口，添加或修改 <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 特性，以便将它的值设置为 InterfaceIsIDispatch。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个类，该类的某个接口与此规则冲突。  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## 相关规则  
 [CA1408：请不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 请参阅  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/zh-cn/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)