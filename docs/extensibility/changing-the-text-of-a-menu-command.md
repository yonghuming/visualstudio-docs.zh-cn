---
title: "更改菜单命令的文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65e7d3d4e3d9a4034a948ee0fa094efbb45b6a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-text-of-a-menu-command"></a>更改菜单命令的文本
以下步骤演示如何通过更改菜单命令的文本标签<xref:System.ComponentModel.Design.IMenuCommandService>服务。  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>更改具有 IMenuCommandService 的菜单命令标签  
  
1.  创建一个名为的 VSIX 项目`MenuText`菜单命令与名为**ChangeMenuText**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  在.vstc 文件中，添加`TextChanges`标志切换为菜单命令，如下面的示例中所示。  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  在 ChangeMenuText.cs 文件中，创建的事件处理程序将在显示的菜单命令之前调用。  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     您还可以通过更改更新此方法中的菜单命令的状态<xref:System.ComponentModel.Design.MenuCommand.Visible%2A>， <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>，和<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A>属性<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>对象。  
  
4.  在 ChangeMenuText 构造函数中，用创建的代码替换原始命令初始化和放置代码<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>(而不是`MenuCommand`)，表示该菜单命令，将添加<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>事件处理程序，并提供菜单给菜单命令服务的命令。  
  
     下面是什么它应如下所示：  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  生成项目并启动调试。 将显示 Visual Studio 的实验实例。  
  
6.  上**工具**菜单您应该看到名为命令**调用 ChangeMenuText**。  
  
7.  单击该命令。 你应看到消息框宣布推出 MenuItemCallback 已被调用。 关闭该消息框，你应看到的工具菜单上的命令的名称现在是**新文本**。
