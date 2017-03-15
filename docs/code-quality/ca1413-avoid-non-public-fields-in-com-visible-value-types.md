---
title: "CA1413：避免在 COM 可见值类型中使用非公共字段 | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413：避免在 COM 可见值类型中使用非公共字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 明确标记为对组件对象模型 \(COM\) 可见的值类型声明非公共实例字段。  
  
## 规则说明  
 对 COM 可见的值类型的非公共实例字段对 COM 客户端可见。  请检查各个字段的内容以查找不应当公开的信息或将对设计或安全性造成意外影响的信息。  
  
 默认情况下，所有的公共值类型都对 COM 可见。  但是，为减少误报，此规则要求显式指定类型的 COM 可见性。  包含程序集必须将 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 设置为 `false` 进行标记，并且类型必须将 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 设置为 `true` 进行标记。  
  
## 如何解决冲突  
 若要修复与该规则的冲突并使字段保持隐藏状态，请将值类型更改为引用类型，或者从类型中移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 特性。  
  
## 何时禁止显示警告  
 如果公开字段是可接受的，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## 相关规则  
 [CA1407：避免在 COM 可见类型中使用静态成员](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 请参阅  
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [为互操作限定 .NET 类型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)