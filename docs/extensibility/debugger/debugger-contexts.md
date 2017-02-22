---
title: "调试器上下文 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK] 上下文"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 调试器上下文
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在调试的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，调试引擎 \(DE\)在不同的上下文中同时运行，如下所示:  
  
-   代码上下文，在程序执行流描述当前位置。  
  
-   文档上下文或位置，描述中的当前位置源文档。  
  
-   表达式计算上下文，介绍上下文表达式计算将发生。  
  
## 本节内容  
 [代码上下文](../../extensibility/debugger/code-context.md)  
 讨论代码上下文作为地址在程序的命令流在今天运行时体系结构方面与非传统的语言，代码可能未由命令表示，但是，某些其他方式来。  
  
 [文档位置](../../extensibility/debugger/document-position.md)  
 定义文档在调试传递一个位置的抽象的 Visual Studio 的位置在源文件中如为 IDE 的地址。  
  
 [文档上下文](../../extensibility/debugger/document-context.md)  
 讨论将在调试有关源文件的 Visual Studio 文档上下文表示。  并讨论符号处理程序如何映射到代码上下文到文档上下文。  
  
 [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)  
 在 Visual Studio 中的表达式计算上下文提供信息。  例如，表达式计算上下文与堆栈帧为计算的局部变量、方法参数和类成员提供上下文。  
  
## 相关章节  
 [调试概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要调试体系结构概念。  
  
 [调试组件](../../extensibility/debugger/debugger-components.md)  
 提供调试组件的 Visual Studio 概述，包括调试引擎 \(DE\)、表达式计算器 \(EE\)和符号处理程序 \(SH\)。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向各种调试任务，如启动程序并计算表达式。