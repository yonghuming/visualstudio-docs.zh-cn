---
title: "将子菜单添加到菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a77cd9504dffc50fd3a3be021cb4e379378f9ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-submenu-to-a-menu"></a>将子菜单添加到菜单
本演练基于中演示[将菜单添加到 Visual Studio 菜单栏](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)通过显示如何将添加到子菜单**TestMenu**菜单。  
  
 子菜单是出现在另一个菜单辅助菜单。 可通过遵循其名称的箭头标识子菜单。 单击名称将导致子菜单和要显示其命令。  
  
 本演练在 Visual Studio 菜单栏上的菜单中创建子菜单，并将新的命令放子菜单。 本演练还实现新的命令。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="adding-a-submenu-to-a-menu"></a>将子菜单添加到菜单  
  
1.  按照中的步骤[将菜单添加到 Visual Studio 菜单栏](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)若要创建的项目和菜单项。 此演练中的步骤假定 VSIX 项目的名称为`TopLevelMenu`。  
  
2.  打开 TestCommandPackage.vsct。 在`<Symbols>`部分中，添加`<IDSymbol>`子菜单、 子菜单的组中，和命令中的所有元素`<GuidSymbol>`节点名为"guidTopLevelMenuCmdSet。" 这是包含的相同节点`<IDSymbol>`顶级菜单的元素。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  添加到新创建的子菜单`<Menus>`部分。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     父级的 GUID/ID 对指定生成中的菜单组[将菜单添加到 Visual Studio 菜单栏](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)，并且是顶级菜单的子级。  
  
4.  添加到步骤 2 中定义的菜单组`<Groups>`部分，并使其成为子子菜单。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  添加新`<Button>`元素`<Buttons>`部分来定义步骤 2 中创建子菜单上的项作为该命令。  
  
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
  
6.  生成解决方案并启动调试。 你应看到实验实例。  
  
7.  单击**TestMenu**若要查看名为的新子菜单**子菜单**。 单击**子菜单**打开子菜单并查看新的命令，**测试子命令**。 请注意，单击**测试子命令**不执行任何操作。  
  
## <a name="adding-a-command"></a>添加命令  
  
1.  打开 TestCommand.cs 并后现有命令 id。 添加下面的命令 ID  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  添加子命令。 找到命令构造函数。 恰好在调用后添加以下行`AddCommand`方法。  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`命令处理程序将在以后定义。 构造函数现在应如下所示：  
  
    ```csharp  
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
  
3.  添加 SubItemCallback()。 这是在单击子菜单中新增的命令时调用的方法。  
  
    ```csharp  
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
  
5.  上**TestMenu**菜单上，单击**子菜单**，然后单击**测试子命令**。 一个消息框应该显示，并显示的文本，"第命令内 TestCommand.SubItemCallback() 测试"。  
  
## <a name="see-also"></a>另请参阅  
 [将菜单添加到 Visual Studio 菜单栏](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)