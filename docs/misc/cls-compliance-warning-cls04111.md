---
title: "CLS 符合性警告 CLS04111 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04111
特性应为“System::Attribute”类型或继承自该类型  
  
 为符合 CLS，自定义特性必须继承 System::Attribute。  向类型应用了非继承自 System::Attribute 的特性。  
  
 以下声明（使用 MSIL 程序集语言）显示可能导致 CLS04111 的原因：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 从 System::Attribute 派生特性可解决此警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```