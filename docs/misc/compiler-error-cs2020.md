---
title: "编译器错误 CS2020 | Microsoft Docs"
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
  - "CS2020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2020"
ms.assetid: b2db7a05-5965-4a9b-86c3-0c4792b29a6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS2020
只有第一组输入文件能生成非“模块”的目标  
  
 在多输出编译中，第一个输出文件必须使用 [\/target: exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md)、[\/target: winexe](../Topic/-target:winexe%20\(C%23%20Compiler%20Options\).md) 或 [\/target: library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md) 生成。 所有后续输出文件必须使用 [\/target: module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 生成。