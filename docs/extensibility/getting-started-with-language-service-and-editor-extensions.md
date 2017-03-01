---
title: "语言服务和编辑器扩展入门 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>语言服务和编辑器扩展入门
编辑器扩展可用于将语言服务功能，如大纲显示、 大括号匹配、 IntelliSense 和灯泡图标添加到您自己的编程语言或任何内容类型。 您还可以自定义外观和行为的 Visual Studio 编辑器中，例如更改颜色、 边距、 修饰和其他可视元素的文本。 您还可以定义自己的类型的内容，然后指定外观和行为的内容将显示的文本视图。  
  
 若要开始编写编辑器扩展，使用作为 Visual Studio SDK 的一部分安装的编辑器项目模板。 Visual Studio SDK 是可下载的一组工具，使其更轻松地开发 Visual Studio 扩展，通过使用 VSPackages 迁移或使用 Managed Extensibility Framework (MEF)。  
  
> [!NOTE]
>  有关 Visual Studio SDK 的详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
 我们建议你了解以下概念和技术编写您自己的编辑器扩展插件之前。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 和编辑器扩展  
 Visual Studio 编辑器用户界面 (UI) 是通过使用 Windows Presentation Foundation (WPF) 实现的。 WPF 提供了丰富的视觉体验和一致的编程模型的业务逻辑分离开来的代码的可视方面。 创建编辑器扩展时，可以使用多个 WPF 元素和功能。 有关详细信息，请参阅[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>托管可扩展性框架 (MEF) 和编辑器扩展  
 Visual Studio 编辑器中使用 Managed Extensibility Framework (MEF) 来管理其组件和扩展。 MEF 还允许开发人员更轻松地创建主机应用程序 Visual Studio 之类的扩展。 在这种框架，您定义根据 MEF 协定的扩展，并将其导出为 MEF 组件部件。 宿主应用程序通过查找它们，注册它们，并确保其应用到正确的上下文管理的组件部分。  
  
> [!NOTE]
>  在编辑器中 MEF 的详细信息，请参阅[在编辑器中 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 编辑器扩展点和扩展  
 编辑器扩展点是 MEF 组件部件; 它们可以自定义和扩展。 在某些情况下您通过实现接口并将其导出正确的元数据以及扩展的扩展点。 在其他情况下您只需声明扩展并将其导出为特定类型。  
  
 以下是一些基本类型的编辑器扩展︰  
  
-   边距和滚动条  
  
-   Tags  
  
-   修饰  
  
-   选项  
  
-   IntelliSense  
  
 编辑器扩展点的详细信息，请参阅[语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)。  
  
## <a name="deploying-editor-extensions"></a>部署编辑器扩展  
 在 Visual Studio 中，您可以通过添加一个名为到解决方案中，生成解决方案时，源 source.extension.vsixmanifest 的元数据文件，然后将已知的文件夹中的二进制文件和清单的副本添加到 Visual Studio 来部署编辑器扩展。 清单文件定义扩展插件 （例如，名称、 作者、 版本和内容类型） 有关的基本情况。 有关 VSIX 清单文件以及如何将扩展部署的详细信息，请参阅[传送 Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md)。  
  
 当在计算机上安装的扩展时，包括二进制文件和清单到 Visual Studio 已知的文件夹的子文件夹中。  
  
> [!WARNING]
>  不需要担心的清单和部署位置的详细信息，如果您使用 Visual Studio 中包含的编辑器可扩展性模板之一。 这些模板包含注册和部署扩展所需的所有内容。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>在实验实例中运行扩展  
 通过将其部署以下实验文件夹 （在 Windows Vista 和 Windows 7） 中开发扩展时，可以防止你的 Visual Studio 的工作版本的影响︰  
  
 *%LOCALAPPDATA%*\VisualStudio\10.0Exp\Extensions\\*公司*\\*扩展 Id*  
  
 其中*%LOCALAPPDATA%*登录的用户的名称*公司*是拥有该扩展，该公司的名称和*扩展 Id*是扩展的 ID。  
  
 在扩展部署到试验性的位置时，它以调试模式运行。 Visual Studio 的第二个实例将启动，并且名为**Microsoft Visual Studio 的实验实例**。  
  
## <a name="managing-extensions"></a>管理扩展  
 Visual Studio 扩展中列出了**扩展和更新**(上**工具**菜单)。 如果您要测试的实验实例中的扩展，则会列出在**扩展和更新**的实验实例中未列出的开发实例。  
  
 有关详细信息，请参阅[查找和使用 Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md)。  
  
## <a name="using-templates-to-create-editor-extensions"></a>使用模板创建编辑器扩展  
 可以使用编辑器模板来创建自定义分类器、 修饰和边距的 MEF 扩展插件。 有 C# 和 Visual Basic 项目的模板。 有关详细信息，请参阅[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
 你还可以使用 VSIX 项目模板来创建扩展插件。 此模板提供只需部署任何类型的扩展，并包括源 source.extension.vsixmanifest 文件、 所需的程序集引用和一个包含允许您将扩展部署的生成任务的项目文件的元素。 有关详细信息，请参阅[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
 您还可以创建编辑器 MEF 组件从 Visual Studio 包扩展。 下面的演练的详细信息，请参阅︰  
  
-   [演练︰ 使用外壳命令与编辑器扩展](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [演练︰ 使用快捷键与编辑器扩展](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)
