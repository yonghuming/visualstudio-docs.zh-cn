---
title: "编译器警告（等级 1）CS1030 | Microsoft Docs"
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
  - "CS1030"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1030"
ms.assetid: 7c565abc-1366-4641-9383-ab8ba026ab96
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 1）CS1030
\#warning：“text”  
  
 显示使用 [\#warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-warning) 指令定义的警告文本。  
  
 下面的示例演示如何创建用户定义的警告：  
  
```  
// CS1030.cs class Sample { static void Main() { #warning Let's give a warning here   // CS1030 } }  
```