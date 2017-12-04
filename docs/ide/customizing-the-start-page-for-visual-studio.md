---
title: "安装自定义起始页或更改 Visual Studio 中的启动项 | Microsoft 文档"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45cfb501103c762f7af6fc130a981028c262540b
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>自定义 Visual Studio 的起始页

可以通过多种不同的方式来自定义 Visual Studio 的启动体验，例如，显示“打开项目”对话框或打开最近加载的解决方案。 你也可以显示自定义起始页，此起始页是在工具窗口中运行的 Windows Presentation Foundation (WPF) XAML 页，并且可以运行 Visual Studio 的内部命令。

## <a name="to-change-the-startup-item"></a>更改启动项

1. 在菜单栏上，依次选择“工具” 、“选项” 。

1. 展开“环境”，然后选择“启动”。

1. 在“启动时”列表中，选择在 Visual Studio 启动后要显示的项目。

## <a name="to-show-a-custom-start-page"></a>显示自定义起始页

可以使用 Visual Studio SDK [创建自己的自定义起始页](../extensibility/creating-a-custom-start-page.md)，或使用其他人已创建的其中一个起始页。 例如，可以在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads) 中查找自定义起始页。

若要安装自定义起始页，请打开 .vsix 文件，或复制起始页文件并将其粘贴到计算机上的 %USERPROFILE%\Documents\Visual Studio 2017\StartPages 文件夹。

### <a name="to-select-which-custom-start-page-to-display"></a>选择要显示的自定义起始页

1. 在菜单栏上，依次选择“工具” 、“选项” 。

1. 展开“环境”，然后选择“启动”。

1. 在“自定义起始页”列表中，选择所需的页。

> [!NOTE]
> 如果自定义起始页中的错误导致 Visual Studio 崩溃，则可以使用安全模式下启动 Visual Studio，然后将其设置为使用默认起始页。 请参阅 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。

## <a name="see-also"></a>请参阅

[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)
