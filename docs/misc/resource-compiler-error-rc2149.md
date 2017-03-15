---
title: "资源编译器错误 RC2149 | Microsoft Docs"
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
  - "RC2149"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2149"
ms.assetid: f0057230-5594-4696-8895-0adab5ba7f64
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 资源编译器错误 RC2149
字符串表中的预期数值常量  
  
 在 `#define` 语句中定义的数值常量必须在后面紧跟 **STRINGTABLE** 语句中的 **BEGIN** 关键字。