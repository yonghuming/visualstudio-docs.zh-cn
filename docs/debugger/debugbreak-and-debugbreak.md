---
title: "DebugBreak 和 __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "断点, DebugBreak 函数"
  - "DebugBreak 函数"
  - "调试 [C++], DebugBreak 函数"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# DebugBreak 和 __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

你可以在代码中的任意点调用 DebugBreak Win32 函数或 [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) 内部类型。  `DebugBreak` 和 `__debugbreak` 具有与在该位置设置断点相同的效果。  
  
 由于 `DebugBreak` 是对系统函数的调用，因此必须安装系统调试符号以确保中断后显示正确的调用堆栈信息。  否则，调试器可能在显示一帧调用堆栈信息后就停止显示。  如果使用 `__debugbreak`，则不需要符号。  
  
## 请参阅  
 [编译器内部函数](/visual-cpp/intrinsics/compiler-intrinsics)   
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)   
 [指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)