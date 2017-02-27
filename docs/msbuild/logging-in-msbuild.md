---
title: "MSBuild 中的日志记录 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 日志记录"
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# MSBuild 中的日志记录
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

日志记录提供了监视生成进度的方法。  日志记录可在日志文件中捕获生成事件、消息、警告和错误。  
  
## 本节内容  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)  
 介绍 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中的日志记录的各个方面。  
  
 [生成记录器](../msbuild/build-loggers.md)  
 概述创建单处理器记录器所需的步骤。  
  
 [多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)  
 介绍日志记录在多处理器环境中的工作方式以及两种多处理器日志记录模型。  
  
 [编写多处理器可识别的记录器](../msbuild/writing-multi-processor-aware-loggers.md)  
 概述如何创建可以识别多处理器的记录器以及如何使用 ConfigurableForwardingLogger。  
  
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)  
 概述如何创建自定义转发记录器。  
  
## 相关章节  
 [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 描述如何通过并行运行 bug 的速度成多个项目。