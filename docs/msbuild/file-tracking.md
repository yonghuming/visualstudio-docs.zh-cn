---
title: "文件跟踪 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 文件跟踪"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 文件跟踪
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文件跟踪日志将会针对某个进程及其子进程调用 Windows 文件系统。  通过调用下面列出的函数，程序可以控制何时打开和关闭此日志记录并指定要使用的日志文件。  
  
## 本节内容  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 停止跟踪当前上下文。  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 调用 [SuspendTracking](../msbuild/suspendtracking.md) 后继续跟踪。  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 设置用于跟踪的线程数。  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 开始新的跟踪上下文。  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 使用指定的根来开始新的跟踪上下文。  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 结束跟踪并释放占用的资源。  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 暂时挂起跟踪。  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 针对所有上下文编写跟踪日志。  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 针对当前上下文编写跟踪日志。