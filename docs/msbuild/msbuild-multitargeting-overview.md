---
title: "MSBuild 多定向概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 多定向概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 MSBuild，您可以将应用程序编译运行在任何一个或多个 .NET Framework 版本中以及任何一个或多个系统平台上。  例如，可以将同一个应用程序编译为既能在 32 位平台的 .NET Framework 2.0 版上运行，也能在 64 位平台的 .NET Framework 4 版上运行。  
  
> [!IMPORTANT]
>  尽管名称为“多目标”，项目一次只能针对一个框架和一个平台。  
  
 一下是 MSBuild 目标的一些功能：  
  
-   可以开发一个基于 .NET Framework 早期版本（例如，版本 2.0、3.0 和 4）的应用程序。  
  
-   可以基于 .NET Framework 之外的框架，例如 Silverlight Framework。  
  
-   可以以一个框架配置文件为目标，该文件是目标框架的预定义子集。  
  
-   如果当前版本的 .NET Framework 发布了一个服务包，则可以使用它。  
  
-   MSBuild 目标功能保证应用程序仅使用目标框架和平台中提供的功能。  
  
## 目标框架和平台  
 *目标框架* 是项目生成运行时使用的 .NET Framework 版本，*目标平台*是项目生成运行时使用的系统平台。例如，您可能希望基于 .NET Framework 2.0 的目标应用程序运行在 32 位平台上使之 802x86 \(“x86 "\) 处理器系列兼容。  目标框架和目标平台的组合称为 *目标上下文*。  有关详细信息，请参阅[目标 Framework 和目标平台](../msbuild/msbuild-target-framework-and-target-platform.md)。  
  
## 工具集 \(ToolsVersion\)  
 工具集是用于创建应用程序的工具、任务和目标的集合。  工具集包括 csc.exe 和 vbc.exe 等编译器、公用目标文件 \(microsoft.common.targets\) 和公用任务文件 \(microsoft.common.tasks\)。  4.5 工具集可用于 .NET Framework 2.0 , 3.0，3.5，4 和 4.5 中。但是，2.0 工具集仅适用于 .NET Framework 2.0 框架。  有关详细信息，请参阅[工具集 \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)。  
  
## 引用程序集  
 在工具集中指定引用程序集可以帮助您设计并生成一个应用程序。  这些引用程序集不仅适用于特定目标的生成，还限制 Visual Studio IDE 中与目标兼容的目标的组件和功能。  有关更多信息，请参阅[在设计时解析程序集](../msbuild/resolving-assemblies-at-design-time.md)。  
  
## 配置目标和任务  
 您可以配置 MSBuild 目和标任务使用 MSBuild 运行在进程，以便可以获得与您正在运行的不同的上下文。例如，那么，当开发计算机在具有 .NET Framework 4.5 时，一个 64 位平台运行针对 32 位，.NET Framework 2.0 应用程序。有关详细信息，请参阅[配置目标和任务](../msbuild/configuring-targets-and-tasks.md)。  
  
## 疑难解答  
 您可能遇到错误，如果您尝试引用不属于目标上下文的程序集。  有关这些错误和如何处理他们的详细信息，请参见 [.NET Framework 目标错误疑难解答](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。