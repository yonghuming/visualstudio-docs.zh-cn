---
title: "配置目标和任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 配置目标和任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以配置 MSBuild 目标和任务去使用 MSBuild 运行进程，以便可以获得与您正在运行的不同的上下文。  例如，那么，当开发计算机在具有64 位平台的.NET Framework 4.5的操作系统运行时，针对 32 位，.NET Framework 2.0 应用程序。  还可以针对 .NET Framework 4 或更早版本的计算机。  组合的 32 \-或 64\-bitness 和特定 .NET Framework 版本称为 *目标上下文*。  
  
## 安装  
 .NET Framework 4.5 和 4.5.1 替换公共语言运行时 \(CLR\)，目标、.NET Framework 4 的任务和工具，而无需在中重命名文件。  .NET Framework 4.5.1 安装属于 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]。  
  
 如果要单独安装 MSBuild 与 Visual Studio，您可以下载安装程序从 [MSBuild 下载](http://go.microsoft.com/fwlink/?LinkId=309745)包。  还必须安装您希望还使用的 .NET Framework 版本。  
  
## 目标和任务  
 MSBuild 运行确定的版本任务处理面向更大量上下文。例如，32 位 MSBuild 可能在针对一个 64 位计算机的64 位进程中运行一个版本任务。  这是由 `UsingTask` 参数和 `Task` 参数控制。  .NET Framework 4.5 安装的目标将这些参数和参数，因此，不需要更改生成到各种目标上下文的应用程序。  
  
 如果要创建自己的目标上下文，必须正确设置这些参数和参数。  查找在 .NET Framework 4.5 Microsoft.Common.targets 文件和 Microsoft.Common.Tasks \(此文件。有关如何创建可与社区目标上下文一起使用的信息或如何修改现有任务的自定义任务，请参见 [如何；配置目标和任务](../msbuild/how-to-configure-targets-and-tasks.md)。  
  
## 请参阅  
 [多目标](../msbuild/msbuild-multitargeting-overview.md)