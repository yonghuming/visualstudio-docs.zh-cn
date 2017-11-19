---
title: "将菜单控制器添加到工具栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786d7c8841f680d5af5c539e30723289df4db0f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>将菜单控制器添加到工具栏
本演练基于[将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)演练并演示如何将菜单控制器添加到工具窗口工具栏。 此处显示的步骤也可以应用于在中创建的工具栏[将工具栏添加](../extensibility/adding-a-toolbar.md)演练。  
  
 菜单控制器是拆分控件。 菜单控制器的左侧显示的最近使用的命令中，并且可以通过单击它运行。 右侧的菜单控制器是一个箭头，单击将打开，其他命令的列表。 当您单击列表中，请在命令运行，命令和它将替换菜单控制器左侧命令。 在这种方式，菜单控制器运行，类似于始终会显示列表中的最近使用的命令的命令按钮。  
  
 菜单控制器可以出现在菜单上，但它们最常用于工具栏上。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-menu-controller"></a>创建菜单控制器  
  
#### <a name="to-create-a-menu-controller"></a>若要创建菜单控制器  
  
1.  请按照中所述的过程[将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)创建有一个工具栏的工具窗口。  
  
2.  在 TWTestCommandPackage.vsct，转到符号部分。 在名为的 GuidSymbol 元素**guidTWTestCommandPackageCmdSet**，声明菜单控制器、 菜单控制器组和三个菜单项。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  在菜单部分中的后的最后一菜单项，定义为一个菜单的菜单控制器。  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges`和`TextIsAnchorCommand`标志必须为包含在内，以启用菜单控制器，以反映所选的最后一个命令。  
  
4.  组中主题的最后一组项后, 添加菜单控制器组。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     通过与父项设置菜单控制器，此组中放置任何命令将显示在菜单控制器中。 `priority`省略属性，这将其设置为默认值为 0，因为它将菜单控制器上的唯一组。  
  
5.  在按钮部分中之后最后一个的按钮条目中，, 为每个菜单项添加一个按钮元素。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  此时，你可以查看菜单控制器。 生成项目并启动调试。 你应看到实验实例。  
  
    1.  上**视图 / 其他窗口**菜单上，打开**测试工具窗口**。  
  
    2.  菜单控制器将显示在工具窗口中的工具栏。  
  
    3.  单击以查看可能的三个命令的菜单控制器右侧的箭头。  
  
     请注意，当你单击的命令，菜单控制器的标题会更改以显示该命令。 在下一步的部分中，我们将添加代码以激活这些命令。  
  
## <a name="implementing-the-menu-controller-commands"></a>实现菜单控制器命令  
  
1.  在 TWTestCommandPackageGuids.cs，现有的命令 Id 的后面添加三个菜单项的命令 Id。  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  在 TWTestCommand.cs，TWTestCommand 类的顶部添加以下代码。  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand 构造函数，在最后一个调用中`AddCommand`方法，添加代码以将路由每个命令通过同一处理程序的事件。  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  将事件处理程序添加到 TWTestCommand 类，以将标记为已检查所选的命令。  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  添加事件处理程序，以显示一个消息框，当用户选择菜单控制器上的命令：  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>测试菜单控制器  
  
1.  生成项目并启动调试。 你应看到实验实例。  
  
2.  打开**测试工具窗口**上**视图 / 其他窗口**菜单。  
  
     菜单控制器将出现在工具窗口中的工具栏并显示**MC 项 1**。  
  
3.  单击箭头左侧的菜单控制器按钮。  
  
     你应该看到三个项，其中第一个已选中，并有周围图标将其突出显示框。 单击**MC 项 3**。  
  
     同时显示消息会出现一个对话框**选择菜单控制器项 3**。 请注意该消息对应于菜单控制器按钮上的文本。 菜单控制器按钮现在显示**MC 项 3**。  
  
## <a name="see-also"></a>另请参阅  
 [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [添加工具栏](../extensibility/adding-a-toolbar.md)