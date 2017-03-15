---
title: "命令行警告 D9042 | Microsoft Docs"
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
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 命令行警告 D9042
搗alue  
  
 在 **\/wd**、**\/we**、**\/wo** 或 **\/wl** 命令行选项中添加了代码分析警告编号，但在不支持代码分析的平台上指定了 **\/analyze** 命令行选项。  若要更正此警告，可改用 x86 版本的 Visual Studio Team System，或者移除 **\/analyze** 命令行选项。  
  
## 示例  
 以下命令行示例在 x64 或 Itanium 系统上生成警告 D9042：  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 若要更正此警告，可改用 x86 版本的 Visual Studio Team System，或者移除 **\/analyze** 和 **\/wd6001** 命令行选项。  
  
## 请参阅  
 [命令行错误 D8000 到 D9999](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [编译器选项](/visual-cpp/build/reference/compiler-options)