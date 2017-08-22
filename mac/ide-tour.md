---
title: "Visual Studio for Mac 教程"
description: "Visual Studio for Mac 提供用于在 macOS 上生成 .NET 应用程序的集成开发环境，包括 ASP.NET Core 网站和适用于 iOS、Android、Mac 和 Xamarin.Forms 的 Xamarin 项目。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 04f7ec6474aafedeccdbbf704486c431a4258f61
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="visual-studio-for-mac-tour"></a>Visual Studio for Mac 教程

Visual Studio for Mac 将 Xamarin 以移动为中心的 IDE 和 Xamarin Studio 发展为 Mac 上的移动优先和云优先的开发环境。 通过这款受开发人员关注的工具，可以利用 .NET 针对用户所需的所有平台创建适用的应用程序。

Visual Studio for Mac 的用户体验 (UX) 与 Windows 版对应产品相似，但前者具有使用本机 macOS 的感觉。 对于之前使用过 Windows 上的 Visual Studio 人的任何人来说，在创建、打开和开发应用时将不会觉得陌生。 此外，Visual Studio for Mac 采用许多强大的工具，将它的 Windows 对应产品打造成十分强大的 IDE。 Roslyn 编译器平台用于重构和 IntelliSense。 它的项目系统和生成引擎使用 MSBuild，它的源编辑器支持 TextMate 包。 对于 Xamarin 和 .NET Core 应用，使用的是相同的调试器引擎，对于 Xamarin.iOS 和 Xamarin.Android 使用的是相同的设计器。

本文探索了 Visual Studio for Mac 的各个部分，并简要介绍了使其成为一款用于创建跨平台应用程序的强大工具的部分功能。

## <a name="ide-tour"></a>IDE 教程

Visual Studio for Mac 分为多个部分，用于管理应用程序文件和设置、创建应用程序代码以及进行调试。

## <a name="welcome-screen"></a>欢迎屏幕

启动时，Visual Studio for Mac 将显示“欢迎屏幕”，如下所示：

![欢迎屏幕](media/ide-tour-image1.png)

欢迎屏幕包含以下部分：

- 工具栏 - 提供到搜索栏的快速访问。 加载解决方案时，工具栏用于设置调试和显示错误相关的应用配置。
- 入门 - 为开始使用 Visual Studio for Mac 的开发人员提供到实用主题的快速访问。
- 最新解决方案 - 提供到最近打开的解决方案的快速访问和用于打开或创建项目的便捷按钮。
- **开发人员新闻** - 有助于了解 Microsoft 开发人员的最新信息的新闻源。

## <a name="solutions-and-projects"></a>解决方案和项目

下图显示加载了应用程序的 Visual Studio for Mac：

![加载了应用程序的 Visual Studio for Mac](media/ide-tour-image17.png)

以下部分概述了 Visual Studio for Mac 中的主要区域。

## <a name="solution-pad"></a>Solution Pad

Solution Pad 在解决方案中组织项目，如下所示：

![在 Solution Pad 中组织的项目](media/ide-tour-image18.png)

在此位置，源代码、资源、用户界面和依赖关系的文件被组织到特定于平台的项目中。

有关在 Visual Studio for Mac 中使用项目和解决方案的详细信息，请参阅[项目和解决方案](~/projects-and-solutions.md)主题。

## <a name="assembly-references"></a>程序集引用
 
下方所示的“引用”文件夹中提供每个项目的程序集引用：

![Solution Pad 中的“引用”文件夹](media/ide-tour-image19.png)

可以使用“编辑引用”对话框添加其他引用，双击“引用”文件夹或在其上下文菜单操作中选择“编辑引用”便可显示该对话框：
 
![“编辑引用”对话框](media/ide-tour-image20.png)

有关在 Visual Studio for Mac 中使用引用的详细信息，请参阅[管理项目中的引用](~/managing-references-in-a-project.md)主题。

## <a name="dependencies--packages"></a>依赖关系/包

在应用中使用的所有外部依赖关系存储在“依赖关系”或“包”文件夹中，具体取决于所在的项目是 .NET Core 还是 Xamarin.iOS/Xamarin.Android 项目。 通常以 NuGet 或组件的形式提供这些内容。

NuGet 是 .NET 开发最常用的程序包管理器。 通过 Visual Studio 的 NuGet 支持，可以轻松地搜索包并将其添加到项目，再添加到应用程序。

若要将依赖关系添加到应用程序，请右键单击“依赖关系”/“包”文件夹，然后选择“添加包”：

![添加 NuGet 包](media/ide-tour-image21.png)

可在[在项目中包括 NuGet 包](~/nuget-walkthrough.md)主题找到在应用程序中使用 NuGet 包的相关信息。

## <a name="refactoring"></a>重构

Visual Studio for Mac 提供用于重构代码的两种有用途径：上下文操作和源分析。 可在[重构](~/refactoring.md)主题中阅读更多相关信息。

## <a name="debugging"></a>调试

Visual Studio for Mac 具有本机调试器，支持 Xamarin.iOS、Xamarin.Mac 和 Xamarin.Android 应用程序的调试。 Visual Studio for Mac 使用 Mono 软调试器，该调试器在 Mono 运行时中实施，以便 IDE 跨所有平台调试托管代码。 有关调试的其他信息，请访问[调试](~/debugging.md)主题。

调试器包含丰富的可视化工具，可用于字符串、颜色、URL、大小、坐标和贝塞尔曲线等特殊类型。

有关调试器的数据可视化效果的详细信息，请访问[数据可视化效果](~/data-visualizations.md)主题。

## <a name="version-control"></a>版本控制

Visual Studio for Mac 与 Git 和 Subversion 源控件系统集成。 源控件下的项目用解决方案名称旁列出的分支表示： 

![分支名称用来表示源控件下的项目](media/ide-tour-image22.png)

未提交更改的文件在解决方案窗格的文件图标上标有注释，如下所示：

![Solution Pad 中的未提交文件](media/ide-tour-image23.png)

有关在 Visual Studio 中使用版本控制的详细信息，请参阅[版本控制](~/version-control.md)主题。
