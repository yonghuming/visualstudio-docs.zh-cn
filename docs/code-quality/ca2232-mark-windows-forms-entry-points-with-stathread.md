---
title: "CA2232：使用 STAThread 标记 Windows 窗体的入口点 | Microsoft Docs"
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
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2232：使用 STAThread 标记 Windows 窗体的入口点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某程序集引用了 <xref:System.Windows.Forms> 命名空间，但没有使用 <xref:System.STAThreadAttribute?displayProperty=fullName> 特性标记该程序集的入口点。  
  
## 规则说明  
 <xref:System.STAThreadAttribute> 指示应用程序的 COM 线程模型是单线程单元。  使用 Windows 窗体的任何应用程序的入口点上必须存在此特性；如果没有此特性，则 Windows 组件可能无法正常工作。  如果不存在此特性，则应用程序使用 Windows 窗体不支持的多线程单元模型。  
  
> [!NOTE]
>  使用应用程序框架的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 项目不必使用 STAThread 标记 **Main** 方法。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编译器会自动进行标记。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将 <xref:System.STAThreadAttribute> 特性添加到入口点。  如果存在 <xref:System.MTAThreadAttribute?displayProperty=fullName> 特性，请移除该特性。  
  
## 何时禁止显示警告  
 如果为不需要并且不支持 <xref:System.STAThreadAttribute> 特性的 .NET Compact Framework 进行开发，则可以安全地禁止显示与该规则有关的警告。  
  
## 示例  
 下面的示例演示 <xref:System.STAThreadAttribute> 的正确用法。  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]