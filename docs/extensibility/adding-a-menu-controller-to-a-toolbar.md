---
title: "将菜单控制器添加到工具栏 | Microsoft Docs"
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
  - "工具栏 [Visual Studio]，添加菜单控制器"
  - "将菜单控制器添加到工具栏菜单"
  - "菜单控制器，将添加到工具栏"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# 将菜单控制器添加到工具栏
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练基于 [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md) 演练中，并演示如何将菜单控制器添加到工具窗口工具栏。 此处显示的步骤也可以将应用到在中创建的工具栏 [将工具栏添加](../extensibility/adding-a-toolbar.md) 演练。  
  
 菜单控制器是拆分控件。 菜单控制器的左侧显示最近使用的命令，并通过单击它可以运行它。 右侧的菜单控制器是一个箭头，单击时，可以打开其他命令的列表。 当您单击某一命令在列表中，这些命令运行，并且它取代了菜单控制器左侧命令。 在这种方式，菜单控制器运行，类似于始终会显示一个列表中的最近使用的命令的命令按钮。  
  
 菜单控制器可以出现在菜单上，但它们最常用于在工具栏上。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建菜单控制器  
  
#### 若要创建菜单控制器  
  
1.  请按照中所述的过程 [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md) 若要创建一个工具窗口，有一个工具栏。  
  
2.  在 TWTestCommandPackage.vsct，转到符号部分。 在名为 GuidSymbol 元素 **guidTWTestCommandPackageCmdSet**, ，声明菜单控制器、 菜单控制器组和三个菜单项。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  在菜单部分中，最后一个菜单项之后, 以菜单的形式定义菜单控制器。  
  
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
  
     `TextChanges` 和 `TextIsAnchorCommand` 标志必须为包含在内，以启用菜单控制器，以反映所选的最后一个命令。  
  
4.  组中部分的最后一组项之后, 添加菜单控制器组。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     通过设置与父菜单控制器，放置在此组中的任何命令将显示在菜单控制器。`priority` 忽略属性，则它将其设置为默认值为 0，因为它将菜单控制器上的唯一组。  
  
5.  在按钮部分中之后的最后一个按钮条目，, 为每个菜单项添加的按钮元素。  
  
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
  
6.  此时，您可以查看菜单控制器。 生成项目并启动调试。 您应该看到的实验实例。  
  
    1.  在 **视图 \/ 其他窗口** 菜单上，打开 **测试工具窗口**。  
  
    2.  在工具窗口工具栏上显示菜单控制器。  
  
    3.  单击以查看可能的三个命令的菜单控制器右侧的箭头。  
  
     注意，当您单击的命令，菜单控制器的标题更改为显示该命令。 在下一部分中，我们将添加代码以激活这些命令。  
  
## 实现菜单控制器命令  
  
1.  在 TWTestCommandPackageGuids.cs，现有的命令 Id 的后面添加三个菜单项的命令 Id。  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  在 TWTestCommand.cs，将以下代码添加 TWTestCommand 类的顶部。  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand 构造函数中，在最后一个调用后 `AddCommand` 方法中，添加代码以将每个命令通过同一处理程序事件路由。  
  
    ```c#  
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
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  添加事件处理程序，其中显示一个消息框，当用户选择菜单控制器上的命令 ︰  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
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
  
## 测试菜单控制器  
  
1.  生成项目并启动调试。 您应该看到的实验实例。  
  
2.  打开 **测试工具窗口** 上 **视图 \/ 其他窗口** 菜单。  
  
     菜单控制器的工具栏中工具窗口中将出现并显示 **MC 第 1 项**。  
  
3.  单击箭头左侧的菜单控制器按钮。  
  
     您应该看到三个项目，其中第一个已选中，并有一个突出显示框来包围它的图标。 单击 **MC 项 3**。  
  
     一个对话框，其中显示消息 **选择菜单控制器项目 3**。 请注意，该消息对应的菜单控制器按钮上的文本。 菜单控制器按钮现在都显示 **MC 项目 3**。  
  
## 请参阅  
 [将工具栏添加到工具窗口](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [将工具栏添加](../extensibility/adding-a-toolbar.md)