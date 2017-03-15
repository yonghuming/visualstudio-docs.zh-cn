---
title: "安装 Visual Studio 2017 RC | Microsoft Docs"
description: "了解如何逐步安装 Visual Studio。"
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63

---
# <a name="install-visual-studio-2017-rc"></a>安装 Visual Studio 2017 RC
欢迎以全新方式安装 Visual Studio！ 在最新版本中，用户可以更轻松地选择并安装所需的功能 — 我们缩减了 Visual Studio 的最小占用空间，使其相比以前安装更快、系统影响更小。  

 想要详细了解 RC 的其他新增功能？ 请参阅我们的[发行说明](https://www.visualstudio.com/news/releasenotes/vs15-relnotes)。 有关我们如何重新设计安装体验的更深入的信息，请参阅我们的博客文章“[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)”（更快、更精简的 Visual Studio 安装程序）和“[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)”（低影响 Visual Studio 安装剖析）。  

 准备安装？ 我们将逐步引导你完成安装。 让我们开始吧。  

## <a name="install-the-installer"></a>安装安装程序  
 下载 Visual Studio 2017 RC 时，将获取一个引导程序文件，用于安装全新的轻型安装程序。 这个新安装程序包含自定义安装所需的所有组件。  

> [!IMPORTANT]
> 如果已在计算机上安装 Visual Studio 2017 的预览版本，系统将会提示在安装 Visual Studio 2017 RC 之前先删除此预览版本。

1.  [下载 Visual Studio Enterprise 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) 并单击“保存”。  然后，从“下载”文件夹中运行 `vs_Enterprise.exe` 文件。  

     如果收到用户帐户控制通知，请单击“是”。  

2.  我们会要求确认 Microsoft [许可条款](https://www.visualstudio.com/support/legal/mt591984)和 Microsoft [隐私声明](https://www.visualstudio.com/dn948229)。 单击“安装”以继续。  

  ![许可条款和隐私声明](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Microsoft 许可条款和隐私声明")  

3.  将出现多个显示安装进度的状态屏幕。 等安装程序完成安装之后，就可以选择所需的功能集或工作负载了。

## <a name="install-workloads"></a>安装工作负载  
 现在，可以使用工作负载自定义你的安装。 选择所需的一个或多个工作负载；每个工作负载均包含首选编程语言或平台所需的功能。  

 下面介绍如何获取它们。  

1.  在“安装 Visual Studio”屏幕中找到所需的工作负载。  

  ![Visual Studio 2017 RC 安装程序对话框](../ide/media/willow1.png "安装 Visual Studio 2017")

     例如，选择 .NET 桌面开发工作负载。 它附带默认核心编辑器，该编辑器针对超过 20 种语言提供基本代码编辑支持，能够打开和编辑任意文件夹中的代码（而无需使用项目），还提供集成的源代码管理。  

2.  选择所需的工作负载后，单击“安装”。  

    接下来，会出现多个显示 Visual Studio 安装进度的状态屏幕。

3.  安装完新的工作负载和组件后，单击“启动”。

## <a name="install-individual-components"></a>安装各个组件

如果不想使用现成的工作负载功能来自定义 Visual Studio 安装，请从 Visual Studio 安装程序中单击“各个组件”选项，选择所需组件，然后按提示操作。

  ![Visual Studio 2017 - 安装各个组件](media/vs2017install-IndividualComponents.PNG "安装 Visual Studio 各个组件")

## <a name="install-language-packs"></a>安装语言包

若要以所选语言安装 Visual Studio 2017 RC，请从 Visual Studio 安装程序中单击“语言包”选项，并按提示操作。

  ![Visual Studio 2017 - 安装语言包](media/vs2017install-LanguagePacks.PNG "安装 Visual Studio 语言包")

### <a name="change-the-installer-language"></a>更改安装程序语言

默认情况下，安装程序首次运行时会尝试匹配操作系统语言。 安装程序将记住此设置。 可通过从命令行运行安装程序来更改此设置。 例如，可以通过运行 `vs_installer.exe --locale en-US`，强制安装程序用英语运行。 安装程序下一次运行时就会记住此设置。 安装程序支持以下语言标记：zh-CN、zh-TW、cs-CZ、en-US、fr-FR、de-DE、it-IT、ja-JP、ko-KR、pl-PL、pt-BR、ru-RU、es-ES 和 tr-TR。


  > [!IMPORTANT]
  > 虽然一般情况下支持在生产环境中使用 Visual Studio 2017 RC，但安装 UI 中标记为“预览”的工作负载和组件不支持在生产环境中使用。

## <a name="see-also"></a>另请参阅  
* [修改 Visual Studio 2017 RC](modify-visual-studio.md)
* [卸载 Visual Studio 2017 RC](uninstall-visual-studio.md)
* [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
* [如何报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


