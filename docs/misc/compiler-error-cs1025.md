---
title: "编译器错误 CS1025 | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1025
应输入单行注释或行尾  
  
 带[预处理器指令](/dotnet/csharp/language-reference/preprocessor-directives/index)的行不能有多行注释。  
  
 以下示例生成 CS1025：  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 如果你尝试某些无效的预处理器指令，也可能发生 CS1025，如下所示：  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```