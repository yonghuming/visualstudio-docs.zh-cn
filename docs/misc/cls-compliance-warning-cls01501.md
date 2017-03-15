---
title: "CLS 合规性警告 CLS01501 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 合规性警告 CLS01501
**varargs 约束不属于 CLS**  
  
 varargs 约束不属于公共语言子集 \(CLS\)。  CLS 支持的唯一调用约定是标准托管调用约定。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下函数声明（使用 MSIL 程序集语言）显示可能导致 CLS01501 的原因：  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 通过使用参数数组，可以解决 CLS01501。  有关详细信息，请参阅 [变量参数列表 \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli)。