---
title: "CLS 符合性警告 CLS04113 | Microsoft Docs"
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
  - "CLS04113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04113"
ms.assetid: 628f56bf-5f2f-4245-b4fd-02d4605a901c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04113
**特性应为“System::Attribute”类型或继承自该类型**  
  
 为符合 CLS，自定义特性必须继承 System::Attribute。  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下声明（使用 MSIL 程序集语言）显示可能导致 CLS04100 的原因：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 从 System::Attribute 派生特性可解决此警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```