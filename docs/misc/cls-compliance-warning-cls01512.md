---
title: "CLS 遵从性警告 CLS01512 | Microsoft Docs"
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
  - "CLS01512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01512"
ms.assetid: 15822eb3-43b1-4d58-a22d-9532e5820008
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 遵从性警告 CLS01512
varargs 约束不属于 CLS  
  
 varargs 约束不属于公共语言子集 \(CLS\)。  CLS 支持的唯一调用约定是标准托管调用约定。  
  
 有关 CLS 遵从性检查的详细信息，请参见[符合 CLS 的程序集](http://msdn.microsoft.com/zh-cn/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 以下函数声明（使用 MSIL 程序集语言）显示可能导致 CLS01512 的原因：  
  
```  
.method public specialname rtspecialname static vararg void  .cctor() cil managed  
```  
  
 通过删除 **vararg** 关键字，可解决此警告：  
  
```  
.method public specialname rtspecialname static void  .cctor() cil managed  
```