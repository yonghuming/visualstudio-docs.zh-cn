---
title: "MSBuild 中的日志记录 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 26a166779ae0a217e9522e7c3b577ec85507c0a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="logging-in-msbuild"></a>MSBuild 中的日志记录
通过日志记录可监视生成的进度。 日志记录捕获日志文件中的生成事件、消息、警告和错误。  
  
## <a name="in-this-section"></a>本节内容  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)  
 描述 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中日志记录的各个方面。  
  
 [生成记录器](../msbuild/build-loggers.md)  
 概述创建单处理器记录器所需的步骤。  
  
 [多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)  
 介绍日志记录在多处理器环境和两个多处理器日志记录模型下的工作原理。  
  
 [编写多处理器感知记录器](../msbuild/writing-multi-processor-aware-loggers.md)  
 概述如何创建多处理器感知记录器以及如何使用可配置的转发记录器。  
  
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)  
 概述如何创建自定义转发记录器。  
  
## <a name="related-sections"></a>相关章节  
 [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 介绍如何通过并行运行多个项目来更快地生成它们。