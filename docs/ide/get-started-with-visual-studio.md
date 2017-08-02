---
title: "Visual Studio 入门 | Microsoft Docs"
description: "了解 Visual Studio 使用入门的基础知识"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 078619c93e18fd25dfbc728d75835f5af58988fe
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="get-started-with-visual-studio"></a>Visual Studio 入门

Visual Studio 是用于开发应用的强大工具。 如果尚未这么做，请下载并安装 [Visual Studio](https://www.visualstudio.com/vs/)。 有关 Visual Studio 下载及其配置方式的详细信息，请观看视频 [Visual Studio 入门 -设置 IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1)。

## <a name="visual-studio-tour"></a>Visual Studio 教程
Visual Studio 提供一组工具窗口、菜单和工具栏，统称为集成的开发环境或 IDE。 Visual Studio IDE 可帮助你完成开发任务。 以下简要概述了可能会经常用到的 IDE 项。

### <a name="code-editor"></a>代码编辑器
这是 Visual Studio 中最常使用的工具窗口之一，可以在该窗口编写、查看和浏览代码。

![代码编辑器](~/ide/media/VSIDE_CodeWindow.png)

利用语句完成、语法着色、地图模式等功能，代码编辑器可帮助你在输入代码时更快、更轻松地编写和查找代码。 有关详细信息，请观看视频 [Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5)（Visual Studio 入门 - 编辑和浏览代码）

某些解决方案类型可能含有名为“窗体”的窗口，例如 Windows Presentation Foundation (WPF) 窗体、Windows 窗体、Extensible Application Markup Language (XAML) 窗体等。 在这些情况下，此位置还会显示一个可视化设计器，让你可以将按钮和列表框等控件拖动到用户运行应用时进行交互的窗体。

### <a name="solution-explorer"></a>“解决方案资源管理器”

称为“解决方案资源管理器”的工具窗口将列出所有代码文件。 解决方案资源管理器可将代码文件分组为解决方案和项目，从而帮助整理代码。 以粗体显示的项目称为启动项目。 它是启动解决方案时运行的第一个代码。 可以更改启动项目。 有关详细信息，请观看视频 [Visual Studio 入门 - IDE 的构建基块](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)。

![解决方案资源管理器折叠节点](~/ide/media/VSIDE_SolutionExplorer2_callouts.png)

 展开项目节点时，除了解决方案和项目，解决方案资源管理器还会列出每个项目中的所有文件。 每个项目包含一个或多个文件，如源代码文件和资源文件（如图像或库）。

![“解决方案资源管理器”](~/ide/media/VSIDE_SolutionExplorer3.png)

若要查看解决方案、项目和文件的属性，请在快捷方式（右键单击）菜单上选择“属性”命令，或选择菜单上的“视图”-“属性”窗口。

![“属性”窗口](~/ide/media/VSIDE_SolutionExplorer4.png)

无需创建解决方案或项目即可开始编写代码。 只需在 Visual Studio 中打开代码文件（如从 Git 存储库克隆的文件）即可立即编辑它们。 这些文件会显示在“解决方案资源管理器”中，并带有语法着色和基本语句完成等，同传统解决方案一样。 请参阅[在 Visual Studio 中开发代码而无需创建项目或解决方案](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)了解详细信息。

### <a name="toolbar-and-menus"></a>工具栏和菜单
若要运行项目、创建新解决方案和保存文件等，请使用 Visual Studio 工具栏和菜单命令。 例如，代码已准备好进行调试时，可以选择工具栏上的“启动”按钮，或选择菜单上的“调试”-“启动调试”。 若要创建新的解决方案，请选择“新建项目”按钮，或选择菜单上的“文件”-“新建”-“项目”等。

![Visual Studio 工具栏](~/ide/media/VSIDE_SolutionExplorer5_callouts.png)

请注意，工具栏图标和菜单命令可能会根据上下文发生更改，表示当前已选中该项。 通过键盘命令以及鼠标可以访问几乎所有的命令。

### <a name="team-explorer"></a>Team Explorer
“团队资源管理器”可用于连接源控件工具（如 [Git](https://git-scm.com/) 和 [Team Foundation 版本控制 (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview)），以在本地存储代码或在托管服务上与他人共享。 还可利用它跟踪任务等。

有关详细信息，请观看视频 [Visual Studio 入门 - IDE 的构建基块](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK)和 [Visual Studio 入门 - 从源控件打开项目](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3)。

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>“输出”窗口
“输出”窗口是 Visual Studio 发送通知（例如，调试和错误消息、编译器警告、发布状态消息等）的位置。 每个消息类型都有自己的选项卡。

![“输出”窗口](~/ide/media/VSIDE_OutputWindow.png)

若要深入了解如何使用“输出”窗口进行调试，请参阅 [The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/)（使用 Visual Studio 进行调试时的“输出”窗口）。

## <a name="first-steps"></a>首要步骤
- **掌握全局** - 概括了解 Visual Studio 中的大部分功能，请参阅教程！ 请参阅 [Visual Studio IDE 功能教程](../ide/visual-studio-ide.md)。
- **安装** - 若要了解如何下载和安装 Visual Studio，请参阅[安装 Visual Studio 2017](../install/install-visual-studio.md)。
- **基础知识** - 若要深入了解 Visual Studio 的工作原理，请参阅[使用 Visual Studio 开发入门](../ide/get-started-developing-with-visual-studio.md)。
- **设置** - 了解如何自定义 Visual Studio，使其符合你习惯的使用方式。 请参阅 [Personalizing the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)（个性化 Visual Studio IDE）。
- **教程** - 若要深入了解如何在 Visual Studio 中开发代码，请浏览教程，如 [Getting Started with Visual C# and Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md)（Visual C# 和 Visual Basic 入门）或 [Getting Started with C++ in Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md)（Visual Studio 中的 C++ 入门）。
- **视频** - 若要深入了解 Visual Studio 的其他功能和特征，请观看 YouTube 上的 [Microsoft Visual Studio 频道](https://www.youtube.com/user/VisualStudio/videos)中的视频、[第 9 频道](https://channel9.msdn.com/Tags/visual+studio)中的 Visual Studio 视频或者 [Microsoft 虚拟学院](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer)中的 Visual Studio 视频。

## <a name="access-cloud-based-resources"></a>访问基于云的资源

如果想在应用或游戏中使用基于云的资源，可以通过包含 [Azure 服务](https://azure.microsoft.com/en-us/services/)达到此目的。 可以通过使用新的 Visual Studio 安装程序安装 **Azure 开发**工作负载来获取 Azure SDK for .NET。 安装的包与 SDK 2.9.5 版本具有相同的功能级别。 对于此版本和所有未来版本的 Visual Studio，只能通过 Visual Studio 安装程序获得 Azure SDK for .NET。

安装 Azure 开发工作负载后，Visual Studio 中会提供名为“Cloud Explorer”的新工具窗口。 Cloud Explorer 可用于在 Visual Studio 中浏览并管理 Azure 资产和资源。 如果某一特定操作需要 Azure 门户，Cloud Explorer 会提供你在 Azure 门户中所需位置的链接。

![Cloud Explorer](~/ide/media/VSIDE_CloudExplorer.png)

若要深入了解如何使用 Cloud Explorer，请参阅[使用 Cloud Explorer 管理 Azure 资源](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/)。
安装 Azure 开发工作负载还会提供 [Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/) 以及其他相关工具。

## <a name="tips-and-tricks"></a>提示和技巧
若要了解快捷方式以及实用提示和技巧，以更好地利用 Visual Studio，请参阅以下内容。
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)（Visual Studio Code 入门 - 提示和技巧）
- [Productivity Tips for Visual Studio](../ide/productivity-tips-for-visual-studio.md)（Visual Studio 的工作效率提示）
- [Visual Studio Tips and Tricks](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)（Visual Studio 提示和技巧）
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)（C++ 调试提示和技巧）
- [Visual Studio's most useful (and underused) tips [Scott Hanselman 的博客]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)（Visual Studio 最有用（且尚未充分利用）的诀窍 [Scott Hanselman 博客]）
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)（Visual Studio 入门 -安装 Visual Studio 扩展）

