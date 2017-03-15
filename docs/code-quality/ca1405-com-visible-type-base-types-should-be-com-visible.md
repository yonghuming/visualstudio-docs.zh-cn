---
title: "CA1405：COM 可见类型的基类型应对 COM 可见 | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405：COM 可见类型的基类型应对 COM 可见
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|类别|Microsoft.Interoperability|  
|是否重大更改|DependsOnFix|  
  
## 原因  
 从非 COM 可见的类型派生的组件对象模型 \(COM\) 可见的类型。  
  
## 规则说明  
 当 COM 可见类型在新版本中添加成员时，必须遵循严格的准则，以避免中断绑定到当前版本的 COM 客户端。  COM 不可见的类型假定在添加新成员时，不需要遵守这些 COM 版本规则。  但是，如果某个 COM 可见类型是从 COM 不可见类型派生的，并公开 <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ClassInterfaceType>（默认值）的类接口，则将向 COM 公开基类型的所有公共成员（除非它们被明确标记为 COM 不可见，但这将是冗余的）。  如果基类型在后续版本中添加新成员，则绑定到派生类型的类接口的所有 COM 客户端都可能会中断。  COM 可见类型只应当从 COM 可见类型派生，以减小中断 COM 客户端的可能性。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请使基类型对于 COM 可见或者使派生类型对于 COM 不可见。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-cn/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)