---
title: "自定义独立的 Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>自定义独立的 Shell
通过更改 Visual Studio 用户界面的各个方面以及通过限制的命令和专用的应用程序中包括的功能，您可以自定义独立的 Visual Studio shell 应用程序。  
  
## <a name="using-the-applicationpkgdef-file"></a>使用 Application.pkgdef 文件  
 独立的 shell 模板解决方案包括*SolutionName*。允许您修改了以下功能的 Application.pkgdef 文件︰  
  
##### <a name="the-application-title"></a>应用程序标题  
 您可以自定义应用程序标题，这是通过更改"AppName"中行的值显示在该应用程序的标题栏的名称*SolutionName*。Application.pkgdef 文件。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
 如果不希望应用程序标题以显示当前已加载的项目，将"ShowHierarchyRootInTitle"行中的值更改*SolutionName*。将文件从 dword:&00000;001 Application.pkgdef 为&00000;000 时表示。  
  
##### <a name="the-application-icon"></a>应用程序图标  
 您可以自定义应用程序图标，它是由应用程序名称的应用程序标题栏中显示的图标。 将不同的图标复制到图标目录。 在**解决方案资源管理器**，将图标添加到资源文件文件夹。 然后打开 VSShellStub.rc 文件并将 IDI_STUBPROGRAM 的值替换为新建图标的名称。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-command-line-logo"></a>命令行的徽标  
 您可以自定义命令行的徽标，它是从命令行中，通过更改中的"CommandLineLogo"行的值来启动应用程序时，将显示的文本*SolutionName*。Application.pkgdef 文件。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>文件的用户的名称的子文件夹  
 您可以更改您的应用程序通过更改中的"UserFilesSubFolderName"行的值来保留用户文件的文件夹名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>在新建项目对话框的解决方案树节点的标题  
 可以通过更改"NewProjDlgSlnTreeNodeTitle"中行的值来自定义的新建项目对话框中的解决方案节点标题*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>在新建项目对话框的已安装的模板标头  
 通过更改"NewProjDlgInstalledTemplatesHdr"中行的值可以更改在新建项目对话框的已安装的模板标头*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>是否默认情况下隐藏的杂项文件  
 您可以指定是否可以通过更改"HideMiscellaneousFilesByDefault"中行的值默认情况下隐藏杂项文件*SolutionName*。Application.pkgdef 文件。 若要隐藏的杂项文件，请将值设置`dword:00000001`，并显示的文件，请将值设置`dword:00000000`。  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>是否要禁用输出窗口  
 您可以指定是否通过更改中的"DisableOutputWindow"行的值来禁用您的应用程序中的输出窗口*SolutionName*。Application.pkgdef 文件。 若要禁用输出窗口，请将值设置`dword:00000001`，若要显示输出窗口，请将该值设置`dword:00000000`。  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>指示是否允许在主窗口的拖放的文件  
 您可以指定是否允许通过更改"AllowsDroppedFilesOnMainWindow"中行的值在您的应用程序的主窗口的拖放的文件*SolutionName*。Application.pkgdef 文件。 若要允许拖放的文件，请将值设置`dword:00000001`，并将值设置为不允许拖放的文件， `dword:00000000`。  
  
##### <a name="the-default-search-page"></a>默认搜索页  
 您可以自定义 web 浏览器页上，打开 web 浏览器窗口，通过更改"DefaultSearchPage"中行的值时显示的页*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-home-page"></a>默认的主页  
 可以通过更改的值中的"DefaultHomePage"行的自定义主页*SolutionName*。Application.pkgdef 文件。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>指示是否隐藏解决方案概念  
 您可以指定是否隐藏您的应用程序中的解决方案，方法是更改的值中的"HideSolutionConcept"行*SolutionName*。Application.pkgdef 文件。 若要隐藏解决方案，请将值设置`dword:00000001`，若要显示该解决方案，请将该值设置`dword:00000000`。  
  
##### <a name="the-default-debug-engine"></a>默认调试引擎  
 你可以通过更改中的"DefaultDebugEngine"行的值来使用您的应用程序的调试引擎*SolutionName*。Application.pkgdef 文件复制到您调试引擎的 GUID。  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>用户选项文件的文件扩展名  
 您可以更改您的应用程序通过更改中的"UserOptsFileExt"行的值来保留用户文件的文件夹名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-solution-file-extension"></a>解决方案文件扩展名  
 你可以更改中的"SolutionFileExt"行的值更改时使用的解决方案文件扩展名*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-user-files-folder-root"></a>默认用户文件文件夹根  
 您可以通过更改"UserFilesSubFolderName"中行的值更改为您的应用程序的用户文件的根文件夹的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-solution-file-creator-identifier"></a>解决方案文件创建者标识符  
 您可以更改中的"SolutionFileCreatorIdentifier"行的值更改时使用的解决方案文件的标识符*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-default-projects-location"></a>默认项目位置  
 您可以通过更改"DefaultProjectsLocation"中行的值来更改默认项目位置的名称*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="the-application-localization-package"></a>应用程序本地化包  
 您可以更改应用程序通过更改"AppLocalizationPackage"中行的值所用的本地化包*SolutionName*。Application.pkgdef 文件。  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>是否要在标题中显示层次结构根  
 您可以指定是否通过更改"ShowHierarchyRootInTitle"中行的值在您的应用程序中的标题栏中显示层次结构根*SolutionName*。Application.pkgdef 文件。 若要显示的层次结构根，请将值设置`dword:00000001`，若要隐藏的层次结构根，请将该值设置`dword:00000000`。  
  
##### <a name="specifying-a-start-page"></a>指定起始页  
 若要在指定应用程序自定义起始页*SolutionName*。Application.pkgdef 文件中，将"DisableStartPage"值设置为`dword:00000000`，并在列表视图`[$RootKey$\StartPage\Default]`设置为相应的.xaml 文件的位置的 URI:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 文件中*SolutionName*UI 项目，注释掉"No_ShellPkg_startPageCommand"条目︰  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 您必须添加相应的.xaml 文件和任何图形所需的文件，为*SolutionName*项目。 实际上，这些文件必须复制到*SolutionName*项目目录中，不会添加一些其他目录中。  
  
 对所有文件、 设置**项类型**属性设置为**独立的 Shell 文件**要复制到的文件顺序*$RootFolder$*目录。 (若要设置**项类型**属性中，右键单击该文件，然后选择**属性**。 此属性可在下找到**配置属性**，**常规**。)  
  
 有关自定义起始页的详细信息，请参阅[自定义起始页](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>使用独立的 shell 的其他元素  
 您可以使用其他文件和独立的 shell 解决方案模板，以进一步自定义您的应用程序中包含的项目。  
  
##### <a name="enabledisable-visual-studio-packages"></a>启用/禁用 Visual Studio 包  
 *SolutionName*.pkgundef 文件，您可以通过排除某些包禁用某些类型的 Visual Studio 功能。 例如，为以下行︰  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 从项目中显示的模板集内移除杂项文件项目**新项目**对话框。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="enabledisable-menu-commands"></a>启用/禁用菜单命令  
 *SolutionName*UI.vsct 文件包括所有可用于独立 shell 的菜单命令的注释掉的列表。 若要禁用给定的命令，请取消注释对应的行。 例如，若要禁用拆分窗口/注释，取消注释`<Define name="No_SplitCommand"/>`行。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>在初始屏幕上使用该位图  
 您可以自定义在初始屏幕，这是启动应用程序，通过更改"SplashScreenBitmap"中行的值时显示的窗口上使用的位图*SolutionName*。Application.pkgdef 文件。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
##### <a name="the-helpabout-window"></a>帮助 / 关于窗口  
 独立的 shell 模板中没有一个单独的项目，可用于自定义帮助 / 关于框中，您的应用程序。 有关详细信息，请参阅[演练︰ 创建基本隔离的 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。
