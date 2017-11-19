---
title: "使用菜单命令创建扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e9f72764d8fc87a9605f3bde20b7b2b93f44f39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-menu-command"></a>使用菜单命令创建扩展
本演练演示如何处理用于启动记事本的菜单命令创建的扩展。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-menu-command"></a>创建菜单命令  
  
1.  创建一个名为的 VSIX 项目**FirstMenuCommand**。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  在项目打开，添加名为的自定义命令项模板**FirstCommand**。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**FirstCommand.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 实验实例有关的详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，打开**工具 / 扩展和更新**窗口。 你应该会看到**FirstMenuCommand**此处扩展。 (如果你打开**扩展和更新**在你的 Visual Studio 工作情况下，不会看到**FirstMenuCommand**)。  
  
     现在请转到**工具**在实验实例中的菜单。 你应该会看到**调用 FirstCommand**命令。 此时它只会显示一个消息框，显示"FirstCommandPackage 内 FirstMenuCommand.FirstCommand.MenuItemCallback()"。 我们将了解如何实际从下一节中的此命令启动记事本。  
  
## <a name="changing-the-menu-command-handler"></a>更改菜单命令处理程序  
 现在让我们更新命令处理程序以启动记事本。  
  
1.  停止调试并返回到 Visual Studio 的你工作实例。 打开 FirstCommand.cs 文件并添加以下 using 语句：  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  找到私有 FirstCommand 构造函数。 这是其中命令挂钩到命令服务和指定的命令处理程序。 将命令处理程序的名称更改为 StartNotepad，，如下所示：  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  删除 MenuItemCallback 方法并添加只需启动记事本的 StartNotepad 方法：  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  现在试一试。当您开始调试项目并单击**工具 / 调用 FirstCommand**，你应看到提出记事本的实例。  
  
     你可以使用的实例<xref:System.Diagnostics.Process>类运行任何可执行文件，而不仅仅是记事本。 使用尝试 calc.exe，例如。  
  
## <a name="cleaning-up-the-experimental-environment"></a>清理实验环境  
 如果你正在开发多个扩展，或只需浏览与扩展代码的不同版本的结果，实验环境可能会停止工作正常的方式。 在这种情况下，应运行重置脚本。 它称为**重置 Visual Studio 2015 实验实例**，和它作为 Visual Studio SDK 的一部分提供。 此脚本删除对你的扩展从实验环境的所有引用，以便可以从头开始。  
  
 你可以对此脚本在两种方式之一：  
  
1.  从桌面，查找**重置 Visual Studio 2015 实验实例**。  
  
2.  从命令行中，运行以下命令：  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>部署你的扩展  
 现在，你有你运行所需的方式的工具扩展，它是时间来考虑与你的好友和同事共享它。 即变得简单，只要它们具有安装的 Visual Studio 2015。 你所要做的就是向他们发送生成的.vsix 文件。 （请确保在发布模式下生成它。）  
  
 你可以在 FirstMenuCommand bin 目录中找到此扩展的.vsix 文件。 具体而言，假定你已生成的发布配置，则将为：  
  
 **\<代码目录 > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 若要安装扩展，您的朋友需要关闭所有打开的实例的 Visual Studio 中，然后双击.vsix 文件，随后会显示**VSIX Installer**。 文件复制到**%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**目录。  
  
 当您的朋友再次将打开 Visual Studio 时，他将查找中的 FirstMenuCommand 扩展**工具 / 扩展和更新**。 他可以转到**扩展和更新**卸载或禁用扩展，太。  
  
## <a name="next-steps"></a>后续步骤  
 本演练说明了仅对 Visual Studio 扩展可以执行的操作一小的部分。 下面是一个可以使用 Visual Studio 扩展执行其他 （相当简单） 操作的简短列表：  
  
1.  你可以执行简单的菜单命令与许多其他操作：  
  
    1.  添加您自己的图标：[将图标添加到菜单命令](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  更改菜单命令的文本：[更改菜单命令的文本](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  将菜单快捷方式添加到命令：[绑定菜单项的键盘快捷方式](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  将不同种类的命令、 菜单和工具栏添加：[扩展菜单和命令](../extensibility/extending-menus-and-commands.md)  
  
3.  添加工具窗口和扩展内置的 Visual Studio 工具窗口：[扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  添加 IntelliSense，代码建议和其他功能的现有代码编辑器：[扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  将选项和属性页和用户设置添加到你的扩展：[扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)和[扩展用户设置和选项](../extensibility/extending-user-settings-and-options.md)  
  
 其他种类的扩展需要稍有更多工作，如创建新的项目类型 ([扩展项目](../extensibility/extending-projects.md))，创建新类型的编辑器 ([创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md))，或在独立 shell 中实现你的扩展： [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)