---
title: "程序节点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程序节点，将调试上下文"
  - "调试 [调试 SDK]，程序节点"
  - "程序节点添加"
  - "程序节点取代"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 程序节点
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根据调试器体系结构， **程序节点**:  
  
-   是程序的轻量说明。  
  
-   确定自身及其正在运行的进程，并且可以附加到，分离并描述创建它，因此，如果任何一种调试引擎 \(DE\)。  
  
-   由 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 接口表示，通常需要创建由、或端口。  程序节点将添加到端口通过调用 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。  当程序节点将添加到端口时，添加到包含程序的进程此过程节点表示。  
  
 某些时，在调试会话基于调试包的实现，开始，程序节点后使用创建相应的程序。  在处理对其过程中查询，程序枚举，则每个程序节点的。  
  
 在程序附加到时， IDE 需要程序的一个轻量说明。  此信息可以从程序节点获得。  一旦程序附加到， IDE 需要显示详细信息，如运行程序中所有线程的列表。  此信息从程序获取。  
  
## 请参阅  
 [Programs](../../extensibility/debugger/programs.md)   
 [进程](../../extensibility/debugger/processes.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)