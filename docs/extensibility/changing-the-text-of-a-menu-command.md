---
title: "更改菜单命令的文本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更改文本的菜单"
  - "文本、 菜单"
  - "更改文本的命令"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# 更改菜单命令的文本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下面的步骤演示如何通过更改菜单命令的文本标签 <xref:System.ComponentModel.Design.IMenuCommandService> 服务。  
  
## 更改具有 IMenuCommandService 的菜单命令标签  
  
1.  创建一个名为的 VSIX 项目 `MenuText` 与菜单命令名为 **ChangeMenuText**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  在.vstc 文件中添加 `TextChanges` 标记，用于您的菜单命令，如下面的示例中所示。  
  
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
  
3.  在 ChangeMenuText.cs 文件中，创建一个事件处理程序将在显示的菜单命令前调用。  
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     此外可以通过更改来更新此方法中的菜单命令的状态 <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, ，<xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, ，和 <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> 属性 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 对象。  
  
4.  在 ChangeMenuText 构造函数中，用创建的代码替换原始命令初始化和放置代码 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(而不是 `MenuCommand`\) 表示的菜单命令，请添加 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件处理程序，并提供到菜单命令服务菜单命令。  
  
     下面是什么它应如下所示︰  
  
    ```c#  
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
  
6.  在 **工具** 菜单上，您应该看到名为命令 **调用 ChangeMenuText**。  
  
7.  单击命令。 您应该看到消息框宣布推出 MenuItemCallback 已被调用。 关闭该消息框，您应看到在工具菜单上命令的名称现在是 **新文本**。