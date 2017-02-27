---
title: "将子菜单添加到菜单 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "上下文菜单"
  - "级联的子菜单"
  - "级联的子菜单"
  - "创建级联的子菜单的菜单"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 43
---
# 将子菜单添加到菜单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练基于中的演示 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 通过演示如何添加子 **TestMenu** 菜单。  
  
 子菜单是出现在另一个菜单中的第二级菜单。 可以通过遵循其名称的箭头标识子菜单。 单击其名称后，子菜单中，要显示其命令。  
  
 本演练将在 Visual Studio 菜单栏上的菜单中创建一个子菜单，并将新的命令放在子菜单。 本演练还实现了新建命令。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 将子菜单添加到菜单  
  
1.  请按照本文 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 以创建的项目和菜单项。 在本演练步骤都假定 VSIX 项目的名称是 `TopLevelMenu`。  
  
2.  打开 TestCommandPackage.vsct。 在 `<Symbols>` 部分中，添加 `<IDSymbol>` 子菜单、 子菜单中组中，和命令中的所有元素 `<GuidSymbol>` 节点名为"guidTopLevelMenuCmdSet。" 这是包含的相同节点 `<IDSymbol>` 顶级菜单的元素。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  添加到新创建的子菜单 `<Menus>` 部分。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     父级的 GUID\/ID 对指定生成中的菜单组 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), ，并且是顶级菜单的子级。  
  
4.  添加到第 2 步中所定义的菜单组 `<Groups>` 部分，然后将它作为子菜单中的子项。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  添加一个新 `<Button>` 元素 `<Buttons>` 部分，以定义在第 2 步中创建作为子菜单上的项的命令。  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  生成解决方案并启动调试。 您应该看到的实验实例。  
  
7.  单击 **TestMenu** 若要查看名为的新子菜单 **子菜单**。 单击 **子菜单** 若要打开子菜单中，以查看新的命令， **测试子命令**。 请注意，单击 **测试子命令** 不执行任何操作。  
  
## 添加命令  
  
1.  打开 TestCommand.cs 并将下面的命令 ID 添加后现有命令 id。  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  添加子命令。 找到命令构造函数。 只需调用后添加以下行 `AddCommand` 方法。  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` 命令处理程序将在以后定义。 构造函数现在应如下所示︰  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  添加 SubItemCallback\(\)。 这是在新建命令的子菜单中单击时调用的方法。  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  生成项目并启动调试。 应显示的实验实例。  
  
5.  在 **TestMenu** 菜单上，单击 **子菜单** ，然后单击 **测试子命令**。 一个消息框应显示，并且显示文本"第命令内 TestCommand.SubItemCallback\(\) 测试"。  
  
## 请参阅  
 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)