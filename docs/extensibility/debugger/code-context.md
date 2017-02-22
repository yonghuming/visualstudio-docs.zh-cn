---
title: "代码上下文 | Microsoft Docs"
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
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 代码上下文
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在调试的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，**代码上下文**:  
  
-   提供一个位置的抽象在代码中如用于调试引擎的地址 \(DE\)。  设置为当天大多数运行时体系结构，代码上下文可视为在程序的命令流的地址。  对非传统的语言，代码可能未由命令表示，代码上下文可以使用其他一些方法表示。  
  
-   描述正在调试的程序的执行流的当前位置。  
  
-   ，仅当程序在断点处停止后，存在。  
  
-   具有关联文档上下文。  
  
-   由 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) 接口实现。  
  
## 请参阅  
 [文档上下文](../../extensibility/debugger/document-context.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)