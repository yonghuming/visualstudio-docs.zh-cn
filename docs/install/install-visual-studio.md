---
title: "安装 Visual Studio 2017 | Microsoft Docs"
description: "了解如何逐步安装 Visual Studio。"
ms.custom: 
ms.date: 05/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 9f7c1d33191adf3fb54cf59cd98ae5fffe14eee4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/31/2017

---
# <a name="install-visual-studio-2017"></a>安装 Visual Studio 2017
欢迎以全新方式安装 Visual Studio！ 在最新版本中，用户可以更轻松地选择并安装所需的功能 - 我们缩减了 Visual Studio 的最小占用空间，使其相比以前安装更快、系统影响更小。

想要详细了解其他新增功能？ 请参阅我们的[发行说明](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)。 有关我们如何重新设计安装体验的更深入信息，请参阅博客文章“[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)”（更快、更精简的 Visual Studio 安装程序）和“[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)”（低影响 Visual Studio 安装剖析）。  

准备安装？ 我们将逐步引导你完成安装。

## <a name="check-system-requirements"></a>查看系统要求
开始之前，请查看[系统要求](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs)，确保计算机已准备好安装 Visual Studio 2017。

## <a name="download-visual-studio"></a>下载 Visual Studio
首先需要下载 Visual Studio。 为此，请单击下面的按钮，单击“保存”，然后单击“打开文件夹”。

 > [!div class="button"]
 > [下载 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="install-the-installer"></a>安装安装程序  
下载 Visual Studio 2017 时，将获取一个引导程序文件，用于安装全新的轻型安装程序。 这个新安装程序包含自定义安装所需的所有组件。  

> [!IMPORTANT]
> 如果已在计算机上安装 Visual Studio 2017 的预览版本，系统将会提示在安装 Visual Studio 2017 之前先删除此预览版本。

1.  在“下载”文件夹中，双击与下列文件之一匹配或类似的引导程序文件：

  * 对于 Visual Studio Enterprise，请运行 **vs_enterprise.exe**
  * 对于 Visual Studio Professional，请运行 **vs_professional.exe**
  * 对于 Visual Studio Community，请运行 **vs_community.exe**  <br><br>

  如果收到用户帐户控制通知，请单击“是”。  

2.  我们会要求确认 Microsoft [许可条款](https://www.visualstudio.com/license-terms/)和 Microsoft [隐私声明](https://go.microsoft.com/fwlink/?LinkID=824704)。 单击 **“继续”**。  

   ![许可条款和隐私声明](~/install/media/vs2017-privacy-and-license-terms.PNG "Microsoft 许可条款和隐私声明")  

将出现多个显示安装进度的状态屏幕。 等安装程序完成安装之后，就可以选择所需的功能集或工作负载了。

## <a name="install-workloads"></a>安装工作负载  
 可使用工作负载自定义安装。 选择所需的一个或多个工作负载；每个工作负载均包含首选编程语言或平台所需的功能。  

 下面介绍获取方法。  

1.  在“安装 Visual Studio”屏幕中找到所需的工作负载。  

  ![Visual Studio 2017 安装程序对话框](~/install/media/vs2017-workloads.PNG "安装 Visual Studio 工作负载")

     例如，选择 .NET 桌面开发工作负载。 它附带默认核心编辑器，该编辑器针对超过 20 种语言提供基本代码编辑支持，能够打开和编辑任意文件夹中的代码（而无需使用项目），还提供集成的源代码管理。  

2.  选择所需的工作负载后，单击“安装”。  

    接下来，会出现多个显示 Visual Studio 安装进度的状态屏幕。

3.  安装完新的工作负载和组件后，单击“启动”。

## <a name="install-individual-components"></a>安装各个组件

如果不想使用现成的工作负载功能来自定义 Visual Studio 安装，请从 Visual Studio 安装程序中单击“各个组件”选项，选择所需组件，然后按提示操作。

  ![Visual Studio 2017 - 安装各个组件](~/install/media/vs2017-components.PNG "安装 Visual Studio 各个组件")

## <a name="install-language-packs"></a>安装语言包

若要以所选语言安装 Visual Studio 2017，请从 Visual Studio 安装程序中单击“语言包”选项，并按提示操作。

  ![Visual Studio 2017 - 安装语言包](~/install/media/vs2017-languages.PNG "安装 Visual Studio 语言包")

### <a name="change-the-installer-language"></a>更改安装程序语言

默认情况下，安装程序首次运行时会尝试匹配操作系统语言。 安装程序会记住此设置。 可通过从命令行运行安装程序来更改此设置。 例如，可以通过运行以下命令来强制安装程序用英语运行：`vs_installer.exe --locale en-US`。 安装程序下一次运行时会记住此设置。 安装程序支持以下语言标记：zh-CN、zh-TW、cs-CZ、en-US、fr-FR、de-DE、it-IT、ja-JP、ko-KR、pl-PL、pt-BR、ru-RU、es-ES 和 tr-TR。

## <a name="get-support"></a>获取支持
有时也会遇到问题。 如果 Visual Studio 安装失败，请参阅 [Visual Studio 2017 安装和升级失败疑难解答](troubleshooting-installation-issues.md)页面，查看疑难解答提示。

## <a name="see-also"></a>请参阅  
* [修改 Visual Studio 2017](modify-visual-studio.md)
* [更新 Visual Studio 2017](update-visual-studio.md)
* [卸载 Visual Studio 2017](uninstall-visual-studio.md)
* [Visual Studio 2017 管理员指南](visual-studio-administrator-guide.md)
* [如何报告 Visual Studio 2017 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

