---
title: "添加大多数最近使用过的子菜单上的列表 | Microsoft Docs"
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
  - "MRU 列表"
  - "菜单、 创建 MRU 列表"
  - "最近使用的"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
caps.handback.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
---
# 添加大多数最近使用过的子菜单上的列表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练基于在演示 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md), ，并演示如何将动态列表添加到一个子菜单。 动态列表窗体创建最近使用过的 \(MRU\) 列表的基础。  
  
 动态菜单列表从开始菜单上的占位符。 每次显示的菜单，Visual Studio 集成的开发环境 \(IDE\) 要求的所有命令都应显示在占位符 VSPackage。 动态列表会在菜单上的任意位置。 但是，动态列表将通常存储，并显示由其自己，位于子菜单或菜单的底部。 通过使用这些设计模式，可以使命令进行扩展和收缩而不会影响菜单上的其他命令的位置的动态列表。 在本演练中，动态 MRU 列表显示在现有子菜单，子菜单中的其余部分分开是一条线的底部。  
  
 从技术上讲，动态列表也应用到工具栏。 但是，我们不鼓励使用情况因为工具栏应保持不变，除非用户执行特定步骤来更改它。  
  
 本演练中创建的每次选择其中一个更改其顺序的四个项目的 MRU 列表 （选定的项目移动到列表的顶部）。  
  
 有关菜单和.vsct 文件的详细信息，请参阅 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 创建扩展  
  
-   请按照中的过程 [将子菜单添加到菜单](../extensibility/adding-a-submenu-to-a-menu.md) 在下面的过程中创建修改的子菜单。  
  
 在本演练中的过程假定 VSPackage 的名称是 `TopLevelMenu`, ，这是在中使用的名称 [添加到 Visual Studio 菜单栏的菜单](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。  
  
## 创建动态项目列表命令  
  
1.  打开 TestCommandPackage.vsct。  
  
2.  在 `Symbols` 部分中，在 `GuidSymbol` 名为 guidTestCommandPackageCmdSet，节点将添加的符号 `MRUListGroup` 组和 `cmdidMRUList` 命令时，，如下所示。  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  在 `Groups` 部分中，在现有的组条目后添加声明的组。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  在 `Buttons` 部分中，添加一个节点之后的现有按钮项表示的新声明的命令。  
  
    ```c#  
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
  
     `DynamicItemStart` 标志，可以使动态生成的命令。  
  
5.  生成项目并开始调试以测试的新建命令显示。  
  
     在 **TestMenu** 菜单上，单击新子菜单， **子菜单**, ，以便显示新建命令， **MRU 占位符**。 在下一个过程中实现命令的动态 MRU 列表后，打开子菜单中的每次将替换此命令标签由该列表。  
  
## 填充 MRU 列表  
  
1.  在 TestCommandPackageGuids.cs，后面的现有命令 Id 中添加以下行 `TestCommandPackageGuids` 类定义。  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  在 TestCommand.cs 中添加以下 using 语句。  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  在最后一次 AddCommand 调用后 TestCommand 构造函数中添加以下代码。`InitMRUMenu` 将在以后定义  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand 类中添加以下代码。 此代码初始化的字符串表示要在 MRU 列表中显示的项的列表。  
  
    ```c#  
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
  
5.  之后 `InitializeMRUList` 方法中，添加 `InitMRUMenu` 方法。 此代码初始化 MRU 列表菜单命令。  
  
    ```c#  
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
  
     MRU 列表中，必须创建每个可能的项的菜单命令对象。 IDE 调用 `OnMRUQueryStatus` MRU 列表，直到没有更多的项目中每个项的方法。 在托管代码中，IDE 知道没有更多的项的唯一方法是首先创建所有可能的项。 如果您希望，您可以通过使用第一次标记为在不可见的其他项 `mc.Visible = false;` 创建菜单命令之后。 这些项可以然后让用户看到更高版本使用 `mc.Visible = true;` 中 `OnMRUQueryStatus` 方法。  
  
6.  之后 `InitMRUMenu` 方法中，添加以下 `OnMRUQueryStatus` 方法。 这是设置为每个 MRU 项文本的处理程序。  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  之后 `OnMRUQueryStatus` 方法中，添加以下 `OnMRUExec` 方法。 这是用于选择 MRU 项目的处理程序。 此方法将所选的项目移至列表的顶部，然后在消息框中显示所选的项目。  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## 测试 MRU 列表  
  
#### 若要测试 MRU 菜单列表  
  
1.  生成项目并开始调试  
  
2.  在 **TestMenu** 菜单上，单击 **调用 TestCommand**。 执行此操作将显示一个消息框，指示已选择该命令。  
  
    > [!NOTE]
    >  需要完成此步骤以强制 VSPackage 以加载并正确显示 MRU 列表。 如果您跳过此步骤中，将不显示 MRU 列表。  
  
3.  在 **测试菜单** 菜单上，单击 **子菜单**。 末尾的子菜单中，分隔符下面显示的四项列表。 当您单击 **项目 3**, ，一个消息框应该出现，并显示该文本，"所选的项目 3"。 （如果未显示的四个项的列表，确保你已按前面的步骤中的说明。）  
  
4.  再次打开子菜单。 请注意， **项目 3** 现在位于列表的顶部和其他项已推送下移一个位置。 单击 **项目 3** 再次并请注意，该消息框仍显示"所选的项目 3"，指示文本已正确地移到新位置以及命令标签。  
  
## 请参阅  
 [动态添加菜单项](../extensibility/dynamically-adding-menu-items.md)