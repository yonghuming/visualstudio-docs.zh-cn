---
title: "CA1900：值类型字段应为可移植字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1900：值类型字段应为可移植字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|类别|Microsoft.Portability|  
|是否重大更改|间断 \- 如果该字段在程序集外部可见。<br /><br /> 无间断 \- 如果该字段在程序集外部不可见。|  
  
## 原因  
 此规则对以下项进行检查：当用显式布局声明的结构封送到 64 位操作系统上的非托管代码时，是否正确对齐。  IA\-64 不允许存取未对齐的内存，如果此冲突未得到修复，进程将崩溃。  
  
## 规则说明  
 具有显式布局，包含未对齐字段的结构将会导致在 64 位操作系统上发生崩溃。  
  
## 如何解决冲突  
 所有小于 8 个字节的字段的偏移量都必须是其大小的倍数，所有不小于 8 个字节的字段的偏移量都必须是 8 的倍数。  另一个解决方案是在适当的情况下使用 `LayoutKind.Sequential`，而不使用 `LayoutKind.Explicit`。  
  
## 何时禁止显示警告  
 只有当此警告出现在错误中时，才应禁止显示它。