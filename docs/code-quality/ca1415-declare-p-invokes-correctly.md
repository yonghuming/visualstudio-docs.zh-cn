---
title: "CA1415：正确声明 P/Invoke | Microsoft Docs"
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
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415：正确声明 P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|类别|Microsoft.Interoperability|  
|是否重大更改|无间断 \- 如果声明该参数的 P\/Invoke 在程序集外部不可见。  间断 \- 如果声明该参数的 P\/Invoke 在程序集外部可见。|  
  
## 原因  
 平台调用方法未正确声明。  
  
## 规则说明  
 平台调用方法访问非托管代码，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Declare` 关键字或使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 定义的。  此规则当前查找针对 Win32 函数、且满足以下条件的平台调用方法声明：这些方法具有指向 OVERLAPPED 结构参数的指针，而对应的托管参数却不是指向 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 结构的指针。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请正确地声明平台调用方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例分别演示了与该规则冲突以及满足该规则的平台调用方法。  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## 请参阅  
 [与非托管代码交互操作](../Topic/Interoperating%20with%20Unmanaged%20Code.md)