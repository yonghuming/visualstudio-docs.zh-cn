---
title: "语言服务和编辑器扩展入门 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e590d6fff715aae33ee757460f2b0ba3df31e6e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>语言服务和编辑器扩展入门
编辑器扩展可用于将语言服务功能，如大纲显示、 大括号匹配、 IntelliSense、 和电灯泡添加到您自己的编程语言或任何内容类型。 你还可以自定义的外观和行为的 Visual Studio 编辑器中，例如着色、 边距、 修饰和其他可视元素的文本。 你还可以定义自己的类型的内容，并指定的外观和行为的你的内容将显示的文本视图。  
  
 若要开始编写编辑器扩展，使用 Visual Studio SDK 的一部分安装的编辑器项目模板。 Visual Studio SDK 是一可下载的一套工具，它可以更轻松地开发 Visual Studio 扩展，通过使用 Vspackage 或通过使用 Managed Extensibility Framework (MEF)。  
  
> [!NOTE]
>  有关 Visual Studio SDK 的详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
 我们建议你了解有关以下概念和技术的，需要在编写自己的编辑器扩展前。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 和编辑器扩展  
 通过使用 Windows Presentation Foundation (WPF) 实现的 Visual Studio 编辑器用户界面 (UI)。 WPF 提供的丰富视觉体验和一致的编程模型的业务逻辑分离开来代码可视方面。 在创建编辑器扩展时，可以使用多个 WPF 元素和功能。 有关详细信息，请参阅[Windows Presentation Foundation](/dotnet/framework/wpf/index)。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed 的 Extensibility Framework (MEF) 和编辑器扩展  
 Visual Studio 编辑器使用 Managed Extensibility Framework (MEF) 来管理其组件和扩展。 MEF 还让开发人员更轻松地创建主机应用程序，如 Visual Studio 扩展。 在此框架中，定义 MEF 协定根据扩展并将其导出为 MEF 组件部分。 主机应用程序通过查找、 注册它们，并确保它们所应用正确的上下文来管理组件的各部分。  
  
> [!NOTE]
>  有关在编辑器中的 MEF 的详细信息，请参阅[在编辑器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 编辑器中扩展点和扩展  
 编辑器扩展点是 MEF 组件部分，你可以自定义和扩展。 在某些情况下你通过实现接口并将其导出正确的元数据以及扩展的扩展点。 在其他情况下你刚刚声明扩展并将其导出为特定类型。  
  
 以下是一些基本种类的编辑器扩展：  
  
-   边距和滚动条  
  
-   Tags  
  
-   修饰  
  
-   选项  
  
-   IntelliSense  
  
 有关编辑器的扩展点的详细信息，请参阅[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)。  
  
## <a name="deploying-editor-extensions"></a>部署编辑器扩展  
 在 Visual Studio 中，你可以通过添加一个名为到解决方案中，构建解决方案，source.extension.vsixmanifest 的元数据文件，然后将已知的文件夹中的二进制文件和清单副本添加到 Visual Studio 部署编辑器扩展。 清单文件定义的扩展 （例如，名称、 作者、 版本和内容类型） 有关的基本情况。 有关 VSIX 清单文件以及如何将扩展部署的详细信息，请参阅[传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)。  
  
 当你的计算机上安装扩展时，包括二进制文件和清单到 Visual Studio 已知的文件夹的子文件夹中。  
  
> [!WARNING]
>  无需担心清单和部署位置的详细信息，如果你使用 Visual Studio 中包含的编辑器可扩展性模板之一。 这些模板包含注册和部署扩展所需的所有内容。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>在实验实例中运行扩展  
 在通过将其部署在以下实验文件夹 （在 Windows Vista 和 Windows 7） 中开发扩展时，可以防止你正在使用 Visual Studio 的版本：  
  
 *%LOCALAPPDATA%*\VisualStudio\10.0Exp\Extensions\\*公司*\\*扩展 Id*  
  
 其中*%LOCALAPPDATA%*是登录的用户的名称*公司*是拥有扩展，该公司的名称和*扩展 Id*是扩展的 ID。  
  
 在扩展部署到实验位置时，它将在调试模式下运行。 Visual Studio 的第二个实例已启动，并且名为**Microsoft Visual Studio 的实验实例**。  
  
## <a name="managing-extensions"></a>管理扩展  
 到 Visual Studio 扩展列在**扩展和更新**(上**工具**菜单)。 如果你要在实验实例中测试扩展，被列入**扩展和更新**在实验实例中，但没有列出开发实例中。  
  
 有关详细信息，请参阅[查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)。  
  
## <a name="using-templates-to-create-editor-extensions"></a>使用模板来创建编辑器扩展  
 编辑器模板可用于创建自定义分类器、 修饰和边距的 MEF 扩展。 有用于 C# 和 Visual Basic 项目模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
 VSIX 项目模板还可用于创建扩展。 此模板提供所需部署任何类型的扩展，并包括 source.extension.vsixmanifest 文件、 所需的程序集引用和包括使你能够部署的生成任务的项目文件元素扩展。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
 你还可以创建编辑器 MEF 组件从 Visual Studio 包扩展。 请参阅下面的演练，有关详细信息：  
  
-   [演练：在编辑器扩展中使用 Shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [演练：在编辑器扩展中使用快捷键](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)