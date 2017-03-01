---
title: "什么是 Visual Studio 2015 SDK 中的新增功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>什么是 Visual Studio 2015 SDK 中的新增功能
Visual Studio SDK 的 Visual Studio 2015、 更新时，Visual Studio 2015 和 Visual Studio 2017 具有以下新的和更新功能。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK 更新 1  
 更新 1 包括工具，以帮助您与颜色主题和 Visual Studio 映像服务协同工作的扩展。  
  
 这些主题位于[VSSDK 实用程序](../extensibility/internals/vssdk-utilities.md)部分︰  
  
-   [颜色主题工具](../extensibility/internals/color-theming-tools.md)帮助您创建和编辑的 Visual Studio 的自定义颜色。  
  
-   [映像服务工具](../extensibility/internals/image-service-tools.md)让您使用 Visual Studio 图像清单文件。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>新方法，可以将 Visual Studio SDK 添加到 Visual Studio  
 启动 Visual Studio 2015 中，不需要单独下载 Visual Studio SDK。 但是，您可以将其安装为属于正常安装过程中，或您可以选择将其安装更高版本上。 当打开或创建 VSIX 解决方案时，Visual Studio 会要求您安装 Visual Studio 扩展性工具。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="new-ways-of-creating-extensions"></a>创建扩展的新方法  
 从 Visual Studio 2015 SDK 开始，可以创建的扩展，具体取决于哪种编程语言正在使用的不同选项。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic  
 对于 C# 和 Visual Basic 中，没有可用于创建 Vspackage、 菜单命令、 工具窗口、 编辑器分类器、 编辑器修饰和编辑器边距扩展项目项模板的一个完整范围。 您可以添加任何或所有这些对象与标准的 VSIX 项目。 有关详细信息，请参见:  
  
-   [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [在编辑器中的项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [使用 VSPackage 创建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage 向导不能再在 C# 或 Visual Basic 中创建扩展。  
  
### <a name="c"></a>C++  
 对于 c + +，VSPackage 向导支持菜单命令、 工具窗口和自定义编辑器。 中为其查找**新项目**中的对话框**Visual c + + / 扩展性**。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>通过 NuGet VS SDK 引用程序集  
 对于更高的可移植性和扩展性项目的共享，您可以使用 VS SDK 引用程序集的 NuGet 版本。  这些是位于[nuget.org](http://www.nuget.org)由发布[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) ，可以轻松地添加到您的项目或通过 Visual Studio 的解决方案**引用 / 管理 NuGet 包**对话框。 可以单独将引用添加到特定的可扩展性的程序集或添加所有 VS SDK 都引用程序集上一次使用 VS SDK[元程序包](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。 若要了解有关 NuGet 的详细信息，请参阅[NuGet 概述](http://docs.nuget.org/)和[使用对话框管理 NuGet 包](http://docs.nuget.org/Consume/Package-Manager-Dialog)。  
  
 当您使用 VS SDK 引用程序集的 NuGet 版本时，另一个用户不需要安装 VS SDK 才能打开并生成您的项目。  NuGet 引用程序集和 VS SDK 生成工具会自动安装在该项目的计算机上。  
  
 VS SDK 项模板作为他们的联系方式使用 NuGet 和生成工具，以便获取默认情况下 NuGet 的好处。  
  
> [!NOTE]
>  您可以继续安装 VS SDK 引用程序集使用与您的项目 (位于\<Visual Studio 安装位置&1;> \ VSSDK\VisualStudioIntegration\Common\Assemblies) 和可扩展性的现有项目不需要进行升级以使用 NuGet 包。  项目**引用 / 添加引用**对话框将继续使用安装 VS SDK 引用程序集。  
>   
>  如果想要修改现有项目以使用 NuGet，请参阅[如何︰ 将 VSPackages 迁移到 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)具有一节介绍了可扩展性项目更新到 NuGet 程序包。  
  
## <a name="light-bulbs"></a>灯泡图标  
 Roslyn 项目提供一个编写扩展代码的最令人兴奋的新方法。 有关详细信息，请参阅[Roslyn](https://github.com/dotnet/Roslyn)。  
  
 电灯泡是随 VSSDK 一起提供的新功能。 它们是用于 Visual Studio 编辑器中，展开它以显示一组代码重构操作或内置代码分析器所发现的问题的修补程序的图标。 有关详细信息，请参阅[演练︰ 显示灯泡图标中建议](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
## <a name="updated-user-experience-guidelines"></a>已更新的用户体验指南  
 为 Visual Studio 设计新的扩展或功能？ 签出的更新和扩展[Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您会发现[颜色令牌](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)，[字体大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)，[对话框布局规范](../extensibility/ux-guidelines/layout-for-visual-studio.md)，和其他指南，您需要与 Visual Studio 无缝地集成新的用户界面。
