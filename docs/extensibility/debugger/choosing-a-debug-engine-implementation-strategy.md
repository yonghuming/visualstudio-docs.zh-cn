---
title: "选择调试引擎实施策略 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎，实施策略"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# 选择调试引擎实施策略
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用运行时体系结构确定调试引擎 \(DE\)实现策略。  调试引擎可以创建定向到要调试的过程中，处理到 Visual Studio 会话调试管理器 \(SDM\)或进程外对两个。  下列准则可帮助您在这三种方法中选择。  
  
## 准则  
 当为进程外到要调试时的 SDM 和过程 DE 是可能的，通常不会这样做。  调用进程边界是相对较慢。  
  
 调试引擎已提供对 Win32 本机运行时环境和对公共语言运行时环境。  如果必须替换这些环境之一的 DE，必须创建、处理与 SDM。  
  
 否则，可以选择创建、之间处理 SDM 或定向到要调试的程序。  考虑重要的 DE 的表达式计算器是否需要对程序符号存储区的常见的访问，因此，符号存储区是否可以负载快速访问的内存。  还请注意以下事项:  
  
-   如果没有许多调用表达式计算器和符号存储区之间，或者，如果符号存储区可以读取到 SDM 内存空间，请创建、定向到 SDM。  ，它附加到程序时，必须返回调试引擎的 CLSID 到 SDM。  SDM 使用此 CLSID 创建 DE 的进程实例。  
  
-   如果 DE 必须调用程序访问符号存储区，请创建、处理的程序。  这种情况下，过程创建 DE 的实例。  
  
## 请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)