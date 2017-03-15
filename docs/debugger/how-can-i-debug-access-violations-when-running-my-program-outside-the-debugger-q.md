---
title: "在调试器外部运行程序时如何调试访问冲突？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "访问冲突调试"
  - "调试 [Visual Studio], 访问冲突"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在调试器外部运行程序时如何调试访问冲突？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 问题描述  
 我的程序在 Visual Studio 环境中运行良好，但在 Windows 操作系统中独立运行时产生访问冲突。  如何调试该问题？  
  
## 解决方案  
 设置[实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)选项并独立运行你的程序，直到发生访问冲突。  然后可以在“访问冲突”对话框中单击“取消”启动调试器。  
  
 请参见知识库文章 Q133174“How to Locate Where a General Protection \(GP\) Fault Occurs”（如何定位通用性保护 \(GP\) 错误的发生位置）。可在 MSDN 库 CD 上或通过搜索 [http:\/\/support.microsoft.com\/](http://support.microsoft.com/) 找到知识库文章。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)