---
title: "编译器错误 CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1541
无效的引用选项：“symbol”\-\- 无法引用目录  
  
 编译器检测到尝试指定一个目录而非特定文件的意图。 例如，当使用 [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) 编译器选项时，必须指定一个文件，而不能指定一个目录。  
  
 例如，将 `/reference:c:\` 传递给编译器会生成 CS1541。