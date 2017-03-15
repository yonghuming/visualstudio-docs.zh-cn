---
title: "CA1811：避免使用未调用的私有代码 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811：避免使用未调用的私有代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 某个私有或内部（程序集级别）成员在程序集中没有调用方，既不是由公共语言运行时调用的，也不是由委托调用的。  该规则不检查下列成员：  
  
-   显式接口成员。  
  
-   静态构造函数。  
  
-   序列化构造函数。  
  
-   使用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 或 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 标记的方法。  
  
-   作为重写的成员。  
  
## 规则说明  
 如果当前发生该规则逻辑标识不能识别的入口点，则该规则会报告误报。  此外，编译器可能向程序集发出不可调用的代码。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除不可调用的代码或者添加调用该成员的代码。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1812：避免未实例化的内部类](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801：检查未使用的参数](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)