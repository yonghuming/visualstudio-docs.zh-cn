---
title: "使用菜单命令创建扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编写 vspackage"
  - "vspackage"
  - "教程"
  - "visual studio 程序包"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 56
---
# 使用菜单命令创建扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何使用来创建一个扩展按钮可启动记事本的菜单命令。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建菜单命令  
  
1.  创建一个名为的 VSIX 项目 **FirstMenuCommand**。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  当项目打开后时，添加一个名为的自定义命令项模板 **FirstCommand**。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义命令**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **FirstCommand.cs**。  
  
3.  生成项目并启动调试。  
  
     将显示 Visual Studio 的实验实例。 有关的实验实例的详细信息，请参阅 [实验实例](../extensibility/the-experimental-instance.md)。  
  
4.  在实验实例中，打开  **工具 \/ 扩展和更新** 窗口。 您应该看到 **FirstMenuCommand** 此处扩展。 \(如果您打开 **扩展和更新** 中的 Visual Studio 工作实例，不会看到 **FirstMenuCommand**\)。  
  
     现在请转到 **工具** 的实验实例中的菜单。 您应该看到 **调用 FirstCommand** 命令。 此时它只会弹出一个消息框，指示"FirstCommandPackage 内 FirstMenuCommand.FirstCommand.MenuItemCallback\(\)"。 我们将了解如何实际下一节中通过此命令启动记事本。  
  
## 更改菜单命令处理程序  
 现在让我们更新命令处理程序以启动记事本。  
  
1.  停止调试并回到您的 Visual Studio 工作实例。 打开 FirstCommand.cs 文件并添加以下 using 语句:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  找到专用 FirstCommand 构造函数。 这是命令挂接到命令服务和命令处理程序将指定的位置。 将命令处理程序的名称更改为 StartNotepad，，如下所示:  
  
    ```c#  
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
  
3.  Remove MenuItemCallback 方法并添加一个 StartNotepad 方法，它只是启动记事本:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  现在试一试。 当您开始调试项目并单击 **工具 \/ 调用 FirstCommand**, ，您应该看到一个提出记事本实例。  
  
     可以使用的一个实例 <xref:System.Diagnostics.Process> 类来运行任何可执行文件，而不仅仅是记事本。 试用，使用 calc.exe 为例。  
  
## 清理实验环境  
 如果您正在开发多个扩展名，或只以探究结果与不同版本的扩展插件代码，您的实验环境可能会停止工作方式。 在这种情况下，您应该运行重置脚本。 它称为 **重置 Visual Studio 2015 实验实例**, ，并随附在 Visual Studio SDK 的一部分。 此脚本删除对您的扩展实验环境中的所有引用，以便您可以从头开始。  
  
 您可以获得此脚本在两种方式之一:  
  
1.  从桌面上，找到 **重置 Visual Studio 2015 实验实例**。  
  
2.  从命令行运行以下命令:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## 部署您的扩展  
 现在，拥有您所需的方式运行的工具扩展，就应该考虑与朋友和同事共享它。 只要它们具有安装 Visual Studio 2015，这是很简单。 您需要做的就是向他们发送您生成的.vsix 文件。 \(请务必在发布模式下生成它。\)  
  
 FirstMenuCommand bin 目录中，可以找到此扩展的.vsix 文件。 具体而言，假设您已生成发布配置，则将为:  
  
 **\< 代码目录 \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 若要安装此扩展，您的朋友需要关闭所有打开的 Visual Studio 实例，然后双击.vsix 文件，这将显示 **VSIX 安装程序**。 这些文件复制到 **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** 目录。  
  
 当您的朋友再次启动 Visual Studio 时，他会发现中的扩展名为 FirstMenuCommand **工具 \/ 扩展和更新**。 他可以前往 **扩展和更新** 卸载或禁用该扩展，太。  
  
## 后续步骤  
 本演练说明了仅对 Visual Studio 扩展可以执行的操作一小的部分。 下面是一个可以执行的 Visual Studio 扩展其他 \(合理方便地\) 操作的简短列表:  
  
1.  您可以执行简单的菜单命令与许多其他操作:  
  
    1.  添加您自己的图标: [将图标添加到菜单命令](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  更改菜单命令的文本: [更改菜单命令的文本](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  将菜单快捷方式添加到命令: [绑定的键盘快捷方式菜单项](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  将不同种类的命令、 菜单和工具栏添加: [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)  
  
3.  添加工具窗口和扩展内置的 Visual Studio 工具窗口: [扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  将 IntelliSense、 代码的建议，以及其他功能添加到现有的代码编辑器: [扩展编辑器和语言服务](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  将选项和属性页和用户设置添加到您的扩展插件: [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md) 和 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)  
  
 其他类型的扩展需要稍微复杂一点，如创建新的项目类型 \([扩展项目](../extensibility/extending-projects.md)\)，创建新的编辑器类型 \([创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)\)，或在隔离的 shell 中实现您的扩展: [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)