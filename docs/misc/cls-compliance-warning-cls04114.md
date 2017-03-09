---
title: "CLS 符合性警告 CLS04114 | Microsoft Docs"
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
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS04114
特性应为“System::Attribute”类型或继承自该类型  
  
 为符合 CLS，自定义特性必须继承 System::Attribute。  向委托应用了未从 System::Attribute 继承的特性。  
  
 有关公共语言子集 \(CLS\) 符合性检查的详细信息，请参阅[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下声明（使用 MSIL 程序集语言）显示可能导致 CLS04100 的原因：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 然后是使用此特性的委托：  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 从 System::Attribute 派生特性可解决此警告：  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```