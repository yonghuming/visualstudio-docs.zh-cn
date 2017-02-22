---
title: "CA2207：以内联方式初始化值类型的静态字段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2207：以内联方式初始化值类型的静态字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某值类型声明了显式静态构造函数。  
  
## 规则说明  
 声明值类型时，会进行一次默认的初始化操作，将所有值类型字段设置为零，并将所有引用类型字段设置为 `null`（在 Visual Basic 中为 `Nothing`）。  只能保证在调用该类型的实例构造函数或静态成员之前运行显式静态构造函数。  因此，如果创建类型时没有调用实例构造函数，将不保证静态构造函数会运行。  
  
 如果所有静态数据都是以内联方式初始化的，且没有声明显式静态构造函数，则 C\# 和 Visual Basic 编译器将向 MSIL 类定义添加 `beforefieldinit` 标志。  编译器还会添加包含静态初始化代码的私有静态构造函数。  该私有静态构造函数保证在访问类型的任何静态字段之前运行。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请在声明它时初始化所有静态数据，并移除静态构造函数。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1810：以内联方式初始化引用类型的静态字段](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)