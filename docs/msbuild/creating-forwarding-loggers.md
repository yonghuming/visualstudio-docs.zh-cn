---
title: "创建转发记录器 | Microsoft Docs"
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
  - "MSBuild, 转发记录器"
  - "MSBuild, 日志记录"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 创建转发记录器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当在多处理器系统上生成项目时，转发记录器允许选择要监视的事件，从而提高了日志记录的效率。  如果不必要的事件过多，则会严重影响中心记录器、降低生成速度并造成日志混乱。通过启用转发记录器，可以防止这一点。  
  
 若要创建转发记录器，您可以首先实现 <xref:Microsoft.Build.Framework.IForwardingLogger> 接口，然后手动实现其方法，也可以使用 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 类及其预配置的方法。  （对于大多数应用程序而言，后一种方法已经足够。）  
  
## 注册并响应事件  
 在辅助生成引擎报告生成事件时，转发记录器会收集有关这些生成事件的信息，辅助生成引擎是在多处理器系统上生成期间主生成进程创建的辅助进程。  然后，转发记录器根据您赋予它的指令选择要转发到中心记录器的事件。  
  
 您必须注册转发记录器以处理要监视的事件。  若要注册事件，记录器必须重写 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 方法。  此方法现在包括一个可选参数 `nodecount`，该参数可以设置为系统中的处理器数量。  （默认情况下，该值为 1。）  
  
 您可以监视的事件的示例包括 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 和 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>。  
  
 在多处理器环境中，事件消息的接收顺序可能是紊乱的。  因此，必须使用转发记录器中的事件处理程序来评估事件，并对其进行编程，才能确定应将哪些事件传递给重定向程序来转发到中心记录器。  为此，您可以使用附加在每条消息上的 <xref:Microsoft.Build.Framework.BuildEventContext> 类来协助标识要转发的事件，然后将这些事件的名称传递给 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 类（或其子类）。  在使用此方法时，无需其他特定的编码即可转发事件。  
  
## 指定转发记录器  
 在将转发记录器编译为程序集后，必须告知 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在生成过程中使用该程序集。  若要实现此目的，请使用 MSBuild.exe 并配以 `/FileLogger`、`/FileLoggerParameters` 和 `/DistributedFileLogger` 开关。  `/FileLogger` 开关可向 MSBuild.exe 指示已直接附加记录器。`/DistributedFileLogger` 开关表示每个节点都有一个日志文件。  若要设置转发记录器上的参数，请使用 `/FileLoggerParameters` 开关。  有关这些开关和其他 MSBuild.exe 开关的更多信息，请参见 [命令行参考](../msbuild/msbuild-command-line-reference.md)。  
  
## 可以识别多处理器的记录器  
 当在多处理器系统上生成项目时，来自每个处理器的生成消息并不会按照统一的顺序自动交错。  您必须使用附加在每条消息上的 <xref:Microsoft.Build.Framework.BuildEventContext> 类来建立消息分组优先级。  有关多处理器生成的更多信息，请参见[多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)。  
  
## 请参阅  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [生成记录器](../msbuild/build-loggers.md)   
 [多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)