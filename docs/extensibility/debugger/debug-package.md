---
title: "调试包 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，包"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 调试包
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试包在 UI 的 Visual Studio shell 和处理所有运行。  它使用调试接口的 Visual Studio 并将该会话连接调试管理器 \(SDM\)。  
  
 中断通过 SDM 开关发送的事件调试器从运行模式中断模式和更改焦点为重大的过程。  调试包跟踪堆栈帧和线程从消息发送给它由事件。  
  
 调试包没有语言或运行时环境依赖项。  实现或修改调试包并不是必需的。  
  
 调试包由 vsdebug.dll 实现。  
  
## 请参阅  
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)   
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [线程](../../extensibility/debugger/threads.md)   
 [调试程序组件](../../extensibility/debugger/debugger-components.md)