---
title: "在 Visual Studio 中编译和生成 | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: dc7a0c10390de67b56a83d2824224bed24125db0
ms.openlocfilehash: 744e1c5a3861a1fbc486a03f158c602fddc4877c
ms.contentlocale: zh-cn
ms.lasthandoff: 07/17/2017

---

# <a name="compiling-and-building-in-visual-studio"></a>在 Visual Studio 中编译和生成

在开发周期内随时从源代码中运行生成创建程序集和可执行的应用程序。 一般情况下，生成过程在许多不同的项目类型（如 Windows、ASP.NET、移动应用和其他类型）中非常相似。 生成过程在诸如 C#、Visual Basic、C++ 和 F# 等编程语言之间也非常相似。 

通过经常生成你的代码，你可以快速识别编译时错误，如不正确的语法、拼错的关键字和类型不匹配项。 还可以通过频繁生成并运行调试版本的代码来快速检测和纠正运行时错误，如逻辑错误和语义错误。  

成功的生成实质上是确认应用程序的源代码包含正确的语法，并且已解决对库、程序集和其他组件的所有静态引用。 这会生成一个应用程序可执行文件，然后可以在[调试环境](../debugger/index.md)中通过各种手动和自动测试[验证代码质量](../test/improve-code-quality.md)，测试该可执行文件以便正常运行。 该应用程序经过完全测试后，你可以编译一个发布版本以部署到你的客户。 有关此过程的简介，请参阅[演练：生成应用程序](../ide/walkthrough-building-an-application.md)。  

在 Visual Studio 产品系列中，有三种方法可用于生成应用程序：Visual Studio IDE、MSBuild 命令行工具和 Visual Studio Team Services 上的 Team Foundation Build：
 
| 生成方法 | 优点 | 
| --- |--- | --- |  
| IDE |- 立即创建生成并在调试程序中对其进行测试。<br />- 运行 C++ 和 C# 项目的多处理器生成。<br />- 自定义生成系统的不同方面。 |
| MSBuild 命令行| - 在无需安装 Visual Studio 的情况下生成项目。<br />- 运行所有项目类型的多处理器生成。<br />- 自定义生成系统的大多数区域。|
| Team Foundation Build | - 自动执行生成过程作为持续集成/持续交付管道的一部分。<br />- 将自动测试应用于每个生成。<br />- 为生成过程采用几乎无限的基于云的资源。<br />- 修改生成工作流，并创建生成活动以执行深层的自定义任务。|  

本节中的文档将详细介绍基于 IDE 的生成过程。 有关其他方法的详细信息，请分别参阅 [MSBuild](../msbuild/msbuild.md) 和[持续集成和部署](https://www.visualstudio.com/docs/build/overview)。

## <a name="overview-of-building-from-the-ide"></a>从 IDE 生成的概述  

创建项目时，Visual Studio 创建了该项目的默认生成配置和包含该项目的解决方案。  这些配置定义如何生成和部署解决方案和项目。 尤其是项目配置，对于目标平台（如 Windows 或 Linux）和生成类型（如调试或发布）必须是唯一的。 但是，你可以根据喜好编辑这些配置，也可以根据需要创建自己的配置。

有关在 IDE 中生成的初次介绍，请参阅[演练：生成应用程序](walkthrough-building-an-application.md)。  

接下来，请参阅[在 Visual Studio 中生成和清理项目和解决方案](building-and-cleaning-projects-and-solutions-in-visual-studio)，了解你可以对过程进行哪些不同方面的自定义设置。 自定义包括[更改输出目录](how-to-change-the-build-output-directory.md)、[指定自定义生成事件](specifying-custom-build-events-in-visual-studio.md)、[管理项目依赖项](how-to-create-and-remove-project-dependencies.md)、[管理生成日志文件](how-to-view-save-and-configure-build-log-files.md)以及[禁止显示编译器警告](how-to-suppress-compiler-warnings.md)。

你还可以浏览各种其他任务：
- [了解生成配置](understanding-build-configurations.md)
- [了解生成平台](understanding-build-platforms.md)
- [管理项目和解决方案属性](managing-project-and-solution-properties.md)。  
- 指定 [C#](how-to-specify-build-events-csharp.md) 和 [Visual Basic](how-to-specify-build-events-visual-basic.md) 中的生成事件。 
- [设置生成选项](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。  
  
## <a name="see-also"></a>另请参阅  

- [生成（编译）网站项目](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   
