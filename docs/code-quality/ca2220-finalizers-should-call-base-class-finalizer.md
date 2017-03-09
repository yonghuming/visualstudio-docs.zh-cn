---
title: "CA2220：终结器应调用基类的终结器 | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220：终结器应调用基类的终结器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 重写 <xref:System.Object.Finalize%2A?displayProperty=fullName> 的类型未调用其基类中的 <xref:System.Object.Finalize%2A> 方法。  
  
## 规则说明  
 终止必须通过继承层次结构传播。  要确保这一点，类型必须从其自身的 <xref:System.Object.Finalize%2A> 方法调用它们的基类 <xref:System.Object.Finalize%2A> 方法。  C\# 编译器自动添加对基类终结器的调用。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请从您的 <xref:System.Object.Finalize%2A> 方法调用基类型的 <xref:System.Object.Finalize%2A> 方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  某些针对公共语言运行时的编译器会将对基类型终结器的调用插入 Microsoft 中间语言 \(MSIL\)。  如果报告与该规则有关的警告，则编译器不会插入该调用，您必须将其添加到您的代码中。  
  
## 示例  
 下面的 Visual Basic 示例演示正确调用其基类中的 <xref:System.Object.Finalize%2A> 方法的 `TypeB` 类型。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## 请参阅  
 [释放模式](../Topic/Dispose%20Pattern.md)