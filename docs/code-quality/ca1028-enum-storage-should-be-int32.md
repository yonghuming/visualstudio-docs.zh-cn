---
title: "CA1028：枚举存储应为 Int32 | Microsoft Docs"
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
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1028：枚举存储应为 Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共枚举的基础类型不是 <xref:System.Int32?displayProperty=fullName>。  
  
## 规则说明  
 枚举是一种值类型，它定义一组相关的已命名常数。  默认情况下，<xref:System.Int32?displayProperty=fullName> 数据类型用来存储常数值。  尽管您可以更改此基础类型，然而对于大多数情况，既不必要，也不建议您这样做。  请注意，使用小于 <xref:System.Int32> 的数据类型不会显著地提高性能。  如果不能使用默认的数据类型，则应使用一种符合公共语言系统 \(CLS\) 的整型：<xref:System.Byte>、<xref:System.Int16>、<xref:System.Int32> 或 <xref:System.Int64>，以确保所有的枚举值都可以用符合 CLS 的编程语言表示。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用 <xref:System.Int32>，除非有大小或兼容性问题。  对于 <xref:System.Int32> 不能足以容纳值的情况，请使用 <xref:System.Int64>。  如果向后兼容性要求较小的数据类型，请使用 <xref:System.Byte> 或 <xref:System.Int16>。  
  
## 何时禁止显示警告  
 只有在需要保持向后兼容性时，才禁止显示与该规则有关的警告。  在应用程序中，不符合该规则通常不会引发问题。  在要求语言互操作性的库中，不符合该规则可能给用户带来负面影响。  
  
## 冲突的示例  
  
### 说明  
 下面的示例演示两个没有使用推荐的基础数据类型的枚举。  
  
### 代码  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## 修复方法的示例  
  
### 说明  
 下面的示例通过将基础数据类型更改为 <xref:System.Int32> 修复前面的冲突。  
  
### 代码  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## 相关规则  
 [CA1008：枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700：不要命名“Reserved”枚举值](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## 请参阅  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>