---
title: "在工具窗口中添加快捷菜单 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81e944d73ae45de1a786a6df27652949a38eec81
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>在工具窗口中添加快捷菜单
本演练将在工具窗口的快捷菜单。 快捷菜单是当用户右键单击按钮、 文本框中或窗口背景时显示。 快捷菜单上的命令的行为与其他菜单或工具栏上的命令相同。 若要支持的快捷菜单，指定在.vsct 文件中，并将其显示在响应的鼠标右键单击。  
  
 工具窗口包含的自定义工具窗口类中继承自的 WPF 用户控件<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。  
  
 本演练演示如何创建作为 Visual Studio 菜单中，通过声明.vsct 文件中的菜单项，然后使用托管包框架来实现它们的类中定义的工具窗口的快捷菜单。 此方法便于访问 Visual Studio 命令、 用户界面元素和自动化对象模型。  
  
 或者，如果你的快捷菜单将不访问 Visual Studio 功能，你可以使用<xref:System.Windows.FrameworkElement.ContextMenu%2A>XAML 元素在用户控件中的属性。 有关详细信息，请参阅[ContextMenu](/dotnet/framework/wpf/controls/contextmenu)。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>创建工具窗口快捷方式菜单包  
  
1.  创建一个名为的 VSIX 项目`TWShortcutMenu`并添加名为的工具窗口模板**快捷菜单**到它。 有关创建工具窗口的详细信息，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="specifying-the-shortcut-menu"></a>指定的快捷菜单  
 快捷菜单，如本演练中所示让用户从用于填充工具窗口的背景的颜色的列表中选择。  
  
1.  在 ShortcutMenuPackage.vsct，在名为 guidShortcutMenuPackageCmdSet，GuidSymbol 元素中查找和声明的快捷菜单、 快捷方式菜单组和菜单选项。 GuidSymbol 元素现在应如下所示：  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  之前的按钮元素，创建菜单元素，然后在它中定义的快捷菜单。  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     快捷菜单不具有父级，因为它不是菜单或工具栏的一部分。  
  
3.  使用组元素，其中包含的快捷菜单项，来创建组元素，并将组关联的快捷菜单。  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  在按钮元素中，定义快捷菜单上的将显示单个命令。 按钮元素应如下所示：  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  在 ShortcutMenuPackageGuids.cs，添加命令的定义设置 GUID、 快捷菜单和菜单项。  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     这些是在 ShortcutMenuPackage.vsct 文件的符号节中定义的相同命令 Id。 上下文组不包括此处因为它仅在.vsct 文件中必需。  
  
## <a name="implementing-the-shortcut-menu"></a>实现的快捷菜单  
 本部分实现的快捷菜单和其命令。  
  
1.  在 ShortcutMenu.cs，工具窗口可获取菜单命令服务，但它所包含的控件无法转换。 以下步骤演示如何创建菜单命令服务可供用户控件。  
  
2.  在 ShortcutMenu.cs，添加以下 using 语句：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  重写该工具窗口 initialize （） 方法以获取菜单命令服务并添加控件，将菜单命令服务传递给构造函数：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  在快捷菜单工具窗口构造函数中，删除将控件添加的行。 构造函数现在应如下所示：  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  在 ShortcutMenuControl.xaml.cs，添加菜单命令服务的私有字段和更改控件构造函数，以使用菜单命令服务。 然后使用菜单命令服务添加上下文菜单命令。 ShortcutMenuControl 构造函数现在应类似下面的代码。 将更高版本定义的命令处理程序。  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  在 ShortcutMenuControl.xaml，添加<xref:System.Windows.UIElement.MouseRightButtonDown>到顶级事件<xref:System.Windows.Controls.UserControl>元素。 XAML 文件现在应如下所示：  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  在 ShortcutMenuControl.xaml.cs，添加事件处理程序的存根。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  将以下代码添加到同一个文件 using 语句：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. 实现`MyToolWindowMouseRightButtonDown`，如下所示的事件。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     这将创建<xref:System.ComponentModel.Design.CommandID>对象的快捷菜单，标识鼠标单击的位置，将在该位置中的快捷菜单打开使用<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>方法。  
  
10. 实现的命令处理程序。  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     在这种情况下，只是一种方法处理的所有菜单项的事件通过标识<xref:System.ComponentModel.Design.CommandID>并相应地设置背景色。 如果菜单项中包含不相关的命令，你应已创建单独的事件处理程序为每个命令。  
  
## <a name="testing-the-tool-window-features"></a>测试工具窗口功能  
  
1.  生成项目并启动调试。 实验实例中出现。  
  
2.  在实验实例中，单击**视图 / 其他窗口**，然后单击**快捷菜单**。 执行此操作应显示工具窗口。  
  
3.  右键单击工具窗口的主体。 应显示快捷菜单具有颜色的列表。  
  
4.  单击快捷菜单上的颜色。 工具窗口背景色应更改为所选颜色。  
  
## <a name="see-also"></a>另请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)