---
redirect_url: shell/customizing-the-isolated-shell
title: "自定义独立的 Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35aab40dbacd814dcec281ff1f3dd529b29d4424
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-isolated-shell"></a>自定义独立的 Shell
通过更改 Visual Studio 用户界面的不同方面和通过限制的命令和专用应用程序中包含的功能，你可以自定义 Visual Studio 独立 shell 应用程序。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 Application.pkgdef 文件  
 独立的 shell 模板解决方案包括*SolutionName*。Application.pkgdef 文件，您可以修改以下功能：  
  
##### <a name="the-application-title"></a>应用程序标题  
 你可以自定义应用程序标题，它是通过更改中的"AppName"行的值显示在应用程序的标题栏的名称*SolutionName*。Application.pkgdef 文件。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果你不想要显示当前已加载的项目的应用程序标题，将"ShowHierarchyRootInTitle"行中的值更改*SolutionName*。将文件从 dword: 00000001 Application.pkgdef 为 00000000 时表示。  
  
##### <a name="the-application-icon"></a>应用程序图标  
 你可以自定义应用程序图标，它是由应用程序名称的应用程序标题栏中显示的图标。 复制到的图标目录的不同的图标。 在**解决方案资源管理器**，将图标添加到资源文件文件夹。 然后打开 VSShellStub.rc 文件并将 IDI_STUBPROGRAM 的值替换为新图标的名称。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令行的徽标  
 你可以自定义命令行的徽标，它是从命令行中，通过更改中的"CommandLineLogo"行的值启动应用程序时，将显示的文本*SolutionName*。Application.pkgdef 文件。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>文件的用户的名称的子文件夹  
 你可以更改你的应用程序为用户文件保持通过更改中的"UserFilesSubFolderName"行的值的文件夹的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>新项目对话框中的解决方案树节点的标题  
 可以通过更改中的"NewProjDlgSlnTreeNodeTitle"行的值自定义的新项目对话框中的解决方案节点标题*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>新项目对话框中的已安装的模板标头  
 您可以通过更改中的"NewProjDlgInstalledTemplatesHdr"行的值更改在新项目对话框中的已安装的模板标头*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>是否默认情况下隐藏杂项文件  
 你可以指定是否通过更改中的"HideMiscellaneousFilesByDefault"行的值默认情况下隐藏杂项文件*SolutionName*。Application.pkgdef 文件。 若要隐藏杂项文件，请将值设置`dword:00000001`，并显示的文件，请将值设置`dword:00000000`。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>是否要禁用输出窗口  
 你可以指定是否通过更改的值中的"DisableOutputWindow"行中禁用你的应用程序中的输出窗口*SolutionName*。Application.pkgdef 文件。 若要禁用输出窗口，请将值设置`dword:00000001`，并以显示输出窗口，请将值设置`dword:00000000`。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>是否允许在主窗口的拖放的文件  
 你可以指定是否允许在你的应用程序的主窗口的拖放的文件通过更改中的"AllowsDroppedFilesOnMainWindow"行的值*SolutionName*。Application.pkgdef 文件。 若要允许拖放的文件，请将值设置`dword:00000001`，并将值设置为不允许拖放的文件， `dword:00000000`。  
  
##### <a name="the-default-search-page"></a>默认搜索页  
 你可以自定义 web 浏览器页面，此页面是打开 web 浏览器窗口，通过更改中的"DefaultSearchPage"行的值时显示的页面*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-home-page"></a>默认主页  
 可以通过更改中的"DefaultHomePage"行的值自定义主页*SolutionName*。Application.pkgdef 文件。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>是否要隐藏解决方案概念  
 你可以指定是否通过更改中的"HideSolutionConcept"行的值隐藏你的应用程序中的解决方案*SolutionName*。Application.pkgdef 文件。 若要隐藏解决方案，请将值设置`dword:00000001`，并以显示该解决方案，请将值设置`dword:00000000`。  
  
##### <a name="the-default-debug-engine"></a>默认调试引擎  
 你可以更改你的应用程序使用通过更改中的"DefaultDebugEngine"行的值的调试引擎*SolutionName*。Application.pkgdef 文件复制到你的调试引擎的 GUID。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>用户选项文件的文件扩展名  
 你可以更改你的应用程序为用户文件保持通过更改中的"UserOptsFileExt"行的值的文件夹的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-solution-file-extension"></a>解决方案文件扩展名  
 你可以更改中的"SolutionFileExt"行的值更改时使用的解决方案文件扩展名*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-user-files-folder-root"></a>默认用户文件文件夹根  
 你可以通过更改中的"UserFilesSubFolderName"行的值更改为你的应用程序的用户文件的根文件夹的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-solution-file-creator-identifier"></a>解决方案文件创建者标识符  
 你可以更改用于你的解决方案文件通过更改中的"SolutionFileCreatorIdentifier"行的值的标识符*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-projects-location"></a>默认项目位置  
 您可以通过更改中的"DefaultProjectsLocation"行的值更改默认项目位置的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-application-localization-package"></a>应用程序本地化包  
 你可以更改更改中的"AppLocalizationPackage"行的值用于你的应用程序本地化包*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>是否要在标题中显示的层次结构根  
 你可以指定是否通过更改中的"ShowHierarchyRootInTitle"行的值在你的应用程序的标题栏中显示的层次结构根*SolutionName*。Application.pkgdef 文件。 若要显示层次结构根，请将值设置`dword:00000001`，并将值设置若要隐藏层次结构根， `dword:00000000`。  
  
##### <a name="specifying-a-start-page"></a>指定起始页  
 若要在指定应用程序自定义起始页*SolutionName*。Application.pkgdef 文件，将"DisableStartPage"值设置为`dword:00000000`，并在列表视图`[$RootKey$\StartPage\Default]`设置为.xaml 文件的位置的 URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 文件中*SolutionName*UI 项目，注释掉"No_ShellPkg_startPageCommand"条目：  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 你必须添加.xaml 文件中和你需要为任何图形文件*SolutionName*项目。 实际必须将这些文件复制到*SolutionName*项目目录中，不从某些其他目录添加。  
  
 对所有文件、 设置**项类型**属性**独立 Shell 文件**顺序文件复制到*$RootFolder$*目录。 (若要设置**项类型**属性，右键单击该文件，然后选择**属性**。 此属性下找不到**配置属性**，**常规**。)  
  
 有关自定义起始页的详细信息，请参阅[自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用独立 shell 的其他元素  
 你可以使用其他文件和独立的 shell 解决方案模板来进一步自定义你的应用程序中包含的项目。  
  
##### <a name="enabledisable-visual-studio-packages"></a>启用/禁用 Visual Studio 包  
 *SolutionName*.pkgundef 文件，可通过排除某些包禁用某些类型的 Visual Studio 功能。 例如，以下行：  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 从项目模板中显示的集合中移除杂项文件项目**新项目**对话框。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>启用/禁用菜单命令  
 *SolutionName*UI.vsct 文件包含所有可用于独立 shell 的菜单命令的注释掉的列表。 若要禁用给定的命令，请取消注释对应的行。 例如，若要禁用窗口/拆分注释，取消注释`<Define name="No_SplitCommand"/>`行。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>在初始屏幕上使用位图  
 你可以自定义在初始屏幕，这是启动应用程序，通过更改中的"SplashScreenBitmap"行的值时，将显示的窗口上使用的位图*SolutionName*。Application.pkgdef 文件。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>帮助 / 关于窗口  
 独立的 shell 模板中没有单独的项目可用于自定义帮助 / 关于你的应用程序的框。 有关更多详细信息，请参阅[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。