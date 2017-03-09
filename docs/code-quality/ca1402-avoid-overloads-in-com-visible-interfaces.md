---
title: "CA1402：避免在 COM 可见接口中进行重载 | Microsoft Docs"
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
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402：避免在 COM 可见接口中进行重载
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 组件对象模型 \(COM\) 可见的接口声明重载方法。  
  
## 规则说明  
 在向 COM 客户端公开重载的方法时，只有第一个方法重载保留其名称。  对于后续重载，将为其指定唯一名称，方法是在其名称后面追加一个下划线字符“\_”和一个与该重载的声明顺序对应的整数。  例如，考虑下列方法。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 这些方法如下所示对 COM 客户端公开。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6 COM 客户端无法实现名称中带有下划线的接口方法。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请重命名重载的方法，并使名称保持唯一。  或者，通过以下方法使该接口对 COM 不可见：将可访问性更改为 `internal`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Friend`），或者应用设置为 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 特性。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的接口和一个满足该规则的接口。  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## 相关规则  
 [CA1413：避免在 COM 可见值类型中使用非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可见类型中使用静态成员](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 请参阅  
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long 数据类型](/dotnet/visual-basic/language-reference/data-types/long-data-type)