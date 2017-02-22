---
title: "CA1008：枚举应具有零值 | Microsoft Docs"
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
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1008：枚举应具有零值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|类别|Microsoft.Design|  
|是否重大更改|无间断 \- 如果提示将 **None** 值添加到无标志枚举。间断 \- 如果提示重命名或移除任何枚举值。|  
  
## 原因  
 未应用 <xref:System.FlagsAttribute?displayProperty=fullName> 的枚举没有定义为零值的成员；或者应用了 <xref:System.FlagsAttribute> 的枚举虽然定义了零值的成员，但其名称不是“None”，或者该枚举定义了多个为零值的成员。  
  
## 规则说明  
 像其他值类型一样，未初始化枚举的默认值为零。  无标志特性的枚举应定义值为零的成员，这样默认值即为该枚举的有效值。  如果合适，将该成员命名为“None”。  否则，将零赋给最常用的成员。  请注意，默认情况下，如果声明中未设置第一个枚举成员的值，则其值为零。  
  
 如果应用了 <xref:System.FlagsAttribute> 的枚举定义零值成员，则其名称应为“None”，以指示枚举中尚未设置值。  出于任何其他目的使用零值成员都与使用 <xref:System.FlagsAttribute> 的目的相背，因为 AND 和 OR 按位运算符对该成员无用。  这意味着，只能为一个成员赋值零。  请注意，如果应用了标志特性的枚举中发生多个零值的成员，则 `Enum.ToString()` 会为非零成员返回不正确结果。  
  
## 如何解决冲突  
 要为未应用标志特性的枚举修复与该规则的冲突，请定义一个零值的成员；这不属于重大更改。  对于定义零值成员的无标志特性枚举，请将该成员命名为“None”，然后删除任何其他零值的成员；这属于重大更改。  
  
## 何时禁止显示警告  
 除以前发布的带有标志特性的枚举外，请不要禁止显示与该规则有关的警告。  
  
## 示例  
 下面的示例演示满足该规则的两个枚举和一个与该规则冲突的枚举 `BadTraceOptions`。  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## 相关规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要命名“Reserved”枚举值](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 请参阅  
 <xref:System.Enum?displayProperty=fullName>