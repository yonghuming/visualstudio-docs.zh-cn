---
title: "CA1411：COM 注册方法应该是不可见的 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411：COM 注册方法应该是不可见的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|类别|Microsoft.Interoperability|  
|是否重大更改|是|  
  
## 原因  
 标记有 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 特性的方法在外部可见。  
  
## 规则说明  
 在向组件对象模型 \(COM\) 注册程序集时，会针对该程序集中的每个 COM 可见类型向注册表中添加项。  标记有 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 和 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 特性的方法分别会在注册和注销过程中被调用，以便运行特定于这些类型的注册\/注销的用户代码。  此代码不应当在这些进程外部调用。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将方法的可访问性更改为 `private` 或 `internal`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Friend`）。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示两个与该规则冲突的方法。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## 相关规则  
 [CA1410：应对 COM 注册方法进行匹配](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 注册程序集](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe（程序集注册工具）](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)