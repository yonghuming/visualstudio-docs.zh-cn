---
title: "什么 &#39; s Visual Studio 2015 SDK 中的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b1fa4647cd5b145d19e2264381b186394be814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>什么 &#39; s Visual Studio 2015 SDK 中的新增功能
Visual Studio SDK 的 Visual Studio 2015、 更新，Visual Studio 2015 和 Visual Studio 2017 具有以下新的和更新功能。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK 更新 1  
 更新 1 包括可帮助你很好地配合的颜色主题和 Visual Studio 映像服务的扩展工具。  
  
 这些主题正在[VSSDK 实用工具](../extensibility/internals/vssdk-utilities.md)部分：  
  
-   [颜色主题工具](../extensibility/internals/color-theming-tools.md)帮助你创建和编辑自定义颜色的 Visual Studio。  
  
-   [映像服务工具](../extensibility/internals/image-service-tools.md)让你使用 Visual Studio 图像清单文件。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>新方法，可以将 Visual Studio SDK 添加到 Visual Studio  
 从 Visual Studio 2015 开始，你不必单独下载 Visual Studio SDK。 相反，你可以将其作为正常安装过程的一部分，或者可以选择以更高版本上安装它。 当你打开或创建 VSIX 解决方案时，Visual Studio 将要求你安装 Visual Studio 扩展性工具。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="new-ways-of-creating-extensions"></a>创建扩展的新方式  
 从 Visual Studio 2015 SDK 开始，必须创建的扩展，具体取决于哪种编程语言使用的不同选项。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic  
 对于 C# 和 Visual Basic 中，没有可用于创建 Vspackage、 菜单命令、 工具窗口、 编辑器分类器、 编辑器修饰和编辑器边距扩展项目项模板的完整范围。 你可以添加任何或所有这些到标准的 VSIX 项目。 有关详细信息，请参见:  
  
-   [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [使用编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [使用 VSPackage 建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage 向导无法再创建 C# 或 Visual Basic 中的扩展。  
  
### <a name="c"></a>C++  
 对于 c + +，VSPackage 向导支持菜单命令、 工具窗口和自定义编辑器。 中为其查找**新项目**中的对话框**Visual c + + / 扩展性**。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>通过 NuGet VS SDK 引用程序集  
 有关增加可移植性和可扩展性项目的共享，你可以使用 VS SDK 引用程序集的 NuGet 版本。  这些都位于[nuget.org](http://www.nuget.org)发布[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)并可以轻松地添加到你的项目或通过 Visual Studio 的解决方案**引用 / 管理 NuGet包**对话框。 可以添加对特定的扩展程序集的单个引用，也可以添加所有 VS SDK 都引用程序集在一次使用 VS SDK[元包](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。 若要了解有关 NuGet 的详细信息，请参阅[NuGet 文档](http://docs.microsoft.com/NuGet)和[包管理器 UI](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI)主题。  
  
 当你使用 VS SDK 引用程序集的 NuGet 版本时，另一个用户不需要安装 VS SDK 以打开并生成你的项目。  NuGet 引用程序集和 VS SDK 生成工具自动将该项目的其计算机上安装。  
  
 VS SDK 项模板将用于其引用的 NuGet 和生成工具，以便获取默认的 NuGet 的好处。  
  
> [!NOTE]
>  你可以继续对你的项目中使用 VS SDK 安装引用程序集 (位于\<Visual Studio 安装位置 > \ VSSDK\VisualStudioIntegration\Common\Assemblies) 和现有扩展性项目不需要为升级为使用 NuGet 包。  项目**引用 / 添加引用**对话框继续使用 VS SDK 安装引用程序集。  
>   
>  如果你想要修改你的现有项目，以便使用 NuGet，请参阅[如何： 将 VSPackages 迁移到 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)具有到 NuGet 程序包更新扩展性项目部分。  
  
## <a name="light-bulbs"></a>灯泡  
 编写扩展代码的最令人兴奋的新方法之一是由 Roslyn 项目提供的。 有关详细信息，请参阅[Roslyn](https://github.com/dotnet/Roslyn)。  
  
 电灯泡是附带 VSSDK 的新功能。 它们是使用在 Visual Studio 编辑器中，展开即可显示一组代码重构操作或通过内置的代码分析器发现问题的修补程序的图标。 有关详细信息，请参阅[演练： 显示灯泡建议](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
## <a name="updated-user-experience-guidelines"></a>已更新的用户体验指南  
 为 Visual Studio 中设计新扩展或功能？ 签出的更新和扩展[Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  你将找到[颜色令牌](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)，[字体大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)，[对话框布局规范](../extensibility/ux-guidelines/layout-for-visual-studio.md)，和你需要将你的新 UI 与 Visual Studio 无缝集成其他指南。