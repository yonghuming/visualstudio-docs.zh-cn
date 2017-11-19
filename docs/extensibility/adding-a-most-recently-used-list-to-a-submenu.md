---
title: "添加最近使用过的子菜单的列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: "46"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d622bd917548666e12eff6d29639f62d3ef4bc1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>最近添加大多数使用子菜单的列表
本演练基于中演示[将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)，并演示如何将动态列表添加到子菜单。 动态列表窗体创建最近使用的 (MRU) 列表的基础。  
  
 动态菜单列表开头菜单上的占位符。 每次显示的菜单，则 Visual Studio 集成的开发环境 (IDE) 要求 VSPackage 应显示在占位符的所有命令。 在菜单上的任何位置发生可以动态列表。 但是，动态列表通常存储和子菜单上或在菜单底部显示本身。 通过使用这些设计模式，你可以启用命令来展开和协定而不会影响菜单上的其他命令的位置的动态的列表。 在此演练中，动态 MRU 列表显示底部的现有子菜单，从子菜单的其余部分是一条线分隔。  
  
 从技术上讲，动态列表还可以应用到工具栏。 但是，我们不建议使用因为工具栏会保持不变，除非用户执行特定的步骤来对其进行更改。  
  
 本演练中创建的每次选择其中一个更改其顺序的四个项 MRU 列表 （选定的项移动到列表的顶部）。  
  
 有关菜单和.vsct 文件的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="creating-an-extension"></a>创建扩展  
  
-   按照中的过程[将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md)在以下过程中创建修改的子菜单。  
  
 本演练中的过程假定 VSPackage 的名称为`TopLevelMenu`，这是在中使用的名称[将菜单添加到 Visual Studio 菜单栏](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。  
  
## <a name="creating-a-dynamic-item-list-command"></a>创建动态项列表命令  
  
1.  打开 TestCommandPackage.vsct。  
  
2.  在`Symbols`部分中，在`GuidSymbol`名为 guidTestCommandPackageCmdSet，节点添加的符号`MRUListGroup`组和`cmdidMRUList`命令时，，如下所示。  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  在`Groups`部分，在现有的组条目后添加声明的组。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  在`Buttons`部分中，添加一个节点以表示新声明的命令，在现有的按钮条目后。  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart`标志允许动态生成的命令。  
  
5.  生成项目并启动调试若要测试新的命令的显示。  
  
     上**TestMenu**菜单上，单击新的子菜单，**子菜单**，以显示新的命令**MRU 占位符**。 在下一个过程中实现动态 MRU 列表的命令后，每当打开子菜单时，将替换此命令标签由该列表。  
  
## <a name="filling-the-mru-list"></a>填充 MRU 列表  
  
1.  在 TestCommandPackageGuids.cs，后面的现有命令 Id 中添加以下行`TestCommandPackageGuids`类定义。  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  在 TestCommand.cs 添加以下 using 语句。  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  在最后一次 AddCommand 调用后 TestCommand 构造函数中添加以下代码。 `InitMRUMenu`将更高版本定义  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand 类中添加以下代码。 此代码初始化的字符串表示要在 MRU 列表中显示的项的列表。  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  后`InitializeMRUList`方法，添加`InitMRUMenu`方法。 此值将初始化 MRU 列表菜单命令。  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     MRU 列表中，必须创建一个用于每个可能的项的菜单命令对象。 IDE 调用`OnMRUQueryStatus`MRU 列表，直到有更多的项中每个项的方法。 在托管代码中，ide 后，若要了解更多的项的唯一方法是首先创建所有可能的项。 如果你想，你可以将标记作为在不可见的其他项首先通过使用`mc.Visible = false;`创建菜单命令后。 这些项可以然后让用户看到更高版本使用`mc.Visible = true;`中`OnMRUQueryStatus`方法。  
  
6.  后`InitMRUMenu`方法，添加以下`OnMRUQueryStatus`方法。 这是设置每个 MRU 项的文本的处理程序。  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  后`OnMRUQueryStatus`方法，添加以下`OnMRUExec`方法。 这是处理程序中选择 MRU 项。 此方法将所选的项移到列表的顶部，然后在消息框中显示选定的项。  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>测试 MRU 列表  
  
#### <a name="to-test-the-mru-menu-list"></a>若要测试 MRU 菜单列表  
  
1.  生成项目并启动调试  
  
2.  上**TestMenu**菜单上，单击**调用 TestCommand**。 执行此操作将显示一个消息框，指示选择了该命令。  
  
    > [!NOTE]
    >  此步骤需要强制 VSPackage 加载并正确显示 MRU 列表。 如果你跳过此步骤，MRU 列表不显示。  
  
3.  上**测试菜单**菜单上，单击**子菜单**。 末尾的子菜单中，分隔符下面显示的四个项列表。 当你单击**项 3**，一个消息框应该显示并显示的文本，"所选的项目 3"。 （如果未显示的四个项的列表，请确保您已按照前面的步骤中的说明。）  
  
4.  再次打开子菜单。 请注意，**项 3**现在位于列表的顶部和其他项均收到推送下移一个位置。 单击**项 3**再次和消息框仍显示"所选项目为 3"的字样，以指示文本已正确移动到新位置以及命令标签。  
  
## <a name="see-also"></a>另请参阅  
 [动态添加菜单项](../extensibility/dynamically-adding-menu-items.md)