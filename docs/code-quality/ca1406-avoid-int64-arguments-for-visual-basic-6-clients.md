---
title: "CA1406：避免对 Visual Basic 6 客户端使用 Int64 参数 | Microsoft Docs"
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
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406：避免对 Visual Basic 6 客户端使用 Int64 参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 明确标记为对组件对象模型 \(COM\) 可见的类型声明了一个采用 <xref:System.Int64?displayProperty=fullName> 参数的成员。  
  
## 规则说明  
 Visual Basic 6 COM 客户端不能访问 64 位整数。  
  
 默认情况下，以下项对 COM 可见：程序集、公共类型、公共类型中的公共实例成员和公共值类型的所有成员。  但是，为了减少误报，此规则要求显式声明类型的 COM 可见性；包含程序集必须用设置为 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 进行标记，类型必须用设置为 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 进行标记。  
  
## 如何解决冲突  
 要修复值始终可以表示为 32 位整数的参数与该规则的冲突，请将该参数的类型更改为 <xref:System.Int32?displayProperty=fullName>。  如果 32 位整数不足以表示该参数的值，则应将该参数的类型更改为 <xref:System.Decimal?displayProperty=fullName>。  请注意，在 <xref:System.Int64> 数据类型的上限范围，<xref:System.Single?displayProperty=fullName> 和 <xref:System.Double?displayProperty=fullName> 的精度都降低。  如果成员不打算对 COM 可见，请用设置为 `false` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 对它进行标记。  
  
## 何时禁止显示警告  
 如果确定 Visual Basic 6 COM 不会访问该类型，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## 相关规则  
 [CA1413：避免在 COM 可见值类型中使用非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可见类型中使用静态成员](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 请参阅  
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long 数据类型](/dotnet/visual-basic/language-reference/data-types/long-data-type)