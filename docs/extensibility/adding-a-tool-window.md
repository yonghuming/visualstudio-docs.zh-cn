---
title: "添加一个工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "教程"
  - "工具窗口"
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 52
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 52
---
# 添加一个工具窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在本演练中，您将学习如何创建工具窗口，然后将其集成到 Visual Studio 中，按以下方式︰  
  
-   将控件添加到工具窗口中。  
  
-   将工具栏添加到工具窗口。  
  
-   将命令添加到工具栏。  
  
-   实现命令。  
  
-   设置工具窗口中的默认位置。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建工具窗口  
  
1.  创建一个名为项目 **FirstToolWin** 使用 VSIX 模板，并将添加一个名为的自定义工具窗口项模板 **FirstToolWindow**。  
  
    > [!NOTE]
    >  有关使用一个工具窗口创建扩展的详细信息，请参阅 [使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## 将控件添加到工具窗口  
  
1.  删除默认控件。 打开 FirstToolWindowControl.xaml 并删除 **Click Me ！** 按钮。  
  
2.  在 **工具箱**, ，展开 **所有 WPF 控件** 部分并拖动 **媒体元素** 控制转移到 **FirstToolWindowControl** 窗体。 选择该控件，然后在 **属性** 窗口中，将此元素的命名 **mediaElement1**。  
  
## 将工具栏添加到工具窗口  
 通过以下方式添加工具栏，您保证其渐变样式和颜色是与 IDE 的其余部分一致的。  
  
1.  在 **解决方案资源管理器**, ，打开 FirstToolWindowPackage.vsct。 .Vsct 文件使用 XML 工具窗口中定义的图形用户界面 \(GUI\) 元素。  
  
2.  在 `<Symbols>` 部分中，找到 `<GuidSymbol>` 节点其 `name` 属性是 `guidFirstToolWindowPackageCmdSet`。 添加以下两个 `<IDSymbol>` 元素的列表与 `<IDSymbol>` 此节点来定义一个工具栏和工具栏组中的元素。  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  上方紧靠 `<Buttons>` 部分中，创建 `<Menus>` 部分如下︰  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     有几种不同的菜单。 此菜单是在工具窗口中，一个工具栏，由定义其 `type` 属性。`guid` 和  `id` 设置构成工具栏上的完全限定 ID。 通常情况下， `<Parent>` 菜单的是包含组。 但是，工具栏被指其自身的上级。 因此，相同的标识符用于 `<Menu>` 和 `<Parent>` 元素。`priority` 属性是只是"0。  
  
4.  工具栏类似于在许多方面的菜单。 例如，就像一个菜单可能会有一组命令，工具栏可能还有组。 （在菜单上的命令组隔开水平线条。 在工具栏上的组没有用分隔 visual 分隔线。）  
  
     添加 `<Groups>` 节，其中包含 `<Group>` 元素。 用于定义组中声明其 ID `<Symbols>` 部分。 添加 `<Groups>` 紧后面部分 `<Menus>` 部分。  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     通过将父 GUID 和 ID 设置为 GUID 和 ID 的工具栏上，您将组添加到工具栏。  
  
## 将命令添加到工具栏  
 将命令添加到工具栏上，显示为一个按钮。  
  
1.  在 `<Symbols>` 节中，在工具栏和工具栏之后组声明声明以下 IDSymbol 元素。  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  添加按钮元素内的 `<Buttons>` 部分。 此元素将显示在工具窗口中，带搜索 （放大镜） 图标中的工具栏。  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  打开 FirstToolWindowCommand.cs 并恰好在现有字段之后的类中添加以下行。  
  
    ```c#  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     执行此操作使您的命令可在代码中。  
  
## 将 MediaPlayer 属性添加到 FirstToolWindowControl  
 工具栏控件的事件处理程序，从您的代码必须能够访问媒体播放器控件，这是 FirstToolWindowControl 类的子类。  
  
 在 **解决方案资源管理器**, ，用鼠标右键单击 FirstToolWindowControl.xaml，单击 **查看代码**, ，并将以下代码添加到 FirstToolWindowControl 类。  
  
```c#  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## 实例化工具窗口和工具栏  
 添加一个工具栏和菜单命令调用 **打开的文件** 对话框，并在播放所选的媒体文件。  
  
1.  打开 FirstToolWindow.cs 并添加以下 `using` 语句。  
  
    ```c#  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  在 FirstToolWindow 类中，添加对 FirstToolWindowControl 控件的公共引用。  
  
    ```c#  
    public FirstToolWindowControl control;  
    ```  
  
3.  在构造函数结束时，向新创建的控件中设置此控制变量。  
  
    ```c#  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  实例化在构造函数的工具栏。  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  这个时候 FirstToolWindow 构造函数应如下所示︰  
  
    ```c#  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  将菜单命令添加到工具栏。 在 FirstToolWindowCommand.cs 类中，添加以下 using 语句  
  
    ```c#  
    using System.Windows.Forms;  
    ```  
  
7.  在 FirstToolWindowCommand 类中，ShowToolWindow\(\) 方法末尾添加下面的代码。 下一节中，将实现按钮处理程序命令。  
  
    ```c#  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### 在工具窗口中实现菜单命令  
  
1.  在 FirstToolWindowCommand 类中，添加按钮处理程序调用的方法， **打开的文件** 对话框。 选择一个文件后，播放媒体文件。  
  
2.  在 FirstToolWindowCommand 类中，添加对 FirstToolWindow 窗口中获取 FindToolWindow\(\) 方法中创建的私有引用。  
  
    ```c#  
    private FirstToolWindow window;  
    ```  
  
3.  更改设置 （以便按钮处理程序命令处理程序可以访问该窗口控件上面定义窗口 ShowToolWindow\(\) 方法。 下面是完整的 ShowToolWindow\(\) 方法。  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  添加按钮处理程序方法。 创建用户指定的媒体文件，若要播放，对 OpenFileDialog，然后播放所选的文件。  
  
    ```c#  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## 设置工具窗口中的默认位置  
 接下来，在 IDE 中为工具窗口中指定的默认位置。 工具窗口中的配置信息已在 FirstToolWindowPackage.cs 文件中。  
  
1.  在 FirstToolWindowPackage.cs，找到 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 特性，可以在 `FirstToolWindowPackage` 类，该类将 FirstToolWindow 类型传递给构造函数。 若要指定默认位置，您必须将更多的参数添加到下面的示例的构造函数。  
  
    ```c#  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     第一个命名的参数是 `Style` ，其值为 `Tabbed`, ，这意味着该窗口将在现有的窗口的选项卡。 停靠的位置由指定 `Window` 参数，这种情况下，n 的 GUID **解决方案资源管理器**。  
  
    > [!NOTE]
    >  有关在 IDE 的窗口类型的详细信息，请参阅 <xref:EnvDTE.vsWindowType>。  
  
## 测试工具窗口  
  
1.  按 f5 键以打开新的 Visual Studio 实验实例生成。  
  
2.  在 **视图** 菜单上，指向 **其他窗口** ，然后单击 **第一个工具窗口**。  
  
     Media player 工具窗口应打开在同一个位置 **解决方案资源管理器**。 如果它仍会出现在同一位置前面所述，重置窗口布局 \(**窗口 \/ 重置窗口布局**\)。  
  
3.  在工具窗口中单击 （它具有搜索图标） 按钮。 选择一个支持声音或视频文件，例如，C:\\windows\\media\\chimes.wav，然后按 **打开**。  
  
     你应该能听到钟声声音。  
  
## 请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)