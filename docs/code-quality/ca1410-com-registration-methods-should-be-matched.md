---
title: "CA1410：应对 COM 注册方法进行匹配 | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410：应对 COM 注册方法进行匹配
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大更改|  
  
## 原因  
 某个类型声明了标记有 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 特性的方法，但未声明标记有 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 特性的方法，或者反过来。  
  
## 规则说明  
 为了让组件对象模型 \(COM\) 客户端能够创建 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类型，首先必须注册该类型。  在注册过程中将调用标记有 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 特性的方法（如果有的话），以运行用户指定的代码。  注销过程中将调用标记有 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 特性的对应方法，以执行与注册方法的操作相反的操作。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请添加对应的注册或注销方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  带注释的代码演示对该冲突的修复。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## 相关规则  
 [CA1411：COM 注册方法应该是不可见的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [向 COM 注册程序集](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe（程序集注册工具）](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)