---
title: "CA1017：用 ComVisibleAttribute 标记程序集 | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017：用 ComVisibleAttribute 标记程序集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某程序集未应用 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 特性。  
  
## 规则说明  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 特性决定 COM 客户端如何访问托管代码。  合理的设计指出程序集将显式指示 COM 可见性。  可以设置整个程序集的 COM 可见性，然后重写各个类型和类型成员的 COM 可见性。  如果该特性不存在，则该程序集的内容对 COM 客户端可见。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将该特性添加到程序集。  如果不希望对程序集对 COM 客户端可见，请应用该特性并将其值设置为 `false`。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  如果希望该程序集可见，请应用该特性，然后将其值设置为 `true`。  
  
## 示例  
 下面的示例演示已应用 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 特性而导致其对 COM 客户端不可见的程序集。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## 请参阅  
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [为互操作限定 .NET 类型](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)