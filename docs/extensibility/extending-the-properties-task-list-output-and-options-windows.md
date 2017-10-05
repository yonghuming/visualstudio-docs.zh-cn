---
title: "扩展属性、 任务列表、 输出和选项 Windows |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5f16658320df87a479d9669fadf269856f80a67a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>扩展属性、 任务列表、 输出和选项 Windows
你可以访问 Visual Studio 中的任何工具窗口。 本演练演示如何将工具窗口有关的信息集成到一个新**选项**页和上的新设置**属性**页上，以及如何将写入到**任务列表**和**输出**windows。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-an-extension-with-a-tool-window"></a>创建一个与工具窗口的扩展  
  
1.  创建一个名为项目**TodoList**使用 VSIX 模板，并添加名为的自定义工具窗口项模板**TodoWindow**。  
  
    > [!NOTE]
    >  有关使用工具窗口创建扩展的详细信息，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="set-up-the-tool-window"></a>设置工具窗口  
 添加在其中键入一个新的 ToDo 项目，若要向其中添加新项列表中，一个按钮和列表框在列表中显示的项的文本框。  
  
1.  在 TodoWindow.xaml，从 UserControl 中删除按钮、 文本框中，和 StackPanel 控件。  
  
    > [!NOTE]
    >  这不会删除**button1_Click**事件处理程序，则将在稍后的步骤中重用。  
  
2.  从**所有 WPF 控件**部分**工具箱**，拖动**画布**控件添加到网格。  
  
3.  拖动**文本框中**、**按钮**，和一个**ListBox**到画布。 排列元素，使文本框和按钮是相同的级别上，列表框填充下面，如下图所示的窗口的其余部分。  
  
     ![完成工具窗口](../extensibility/media/t5-toolwindow.png "T5 工具窗口")  
  
4.  在 XAML 窗格中，找到按钮，并将其内容的属性设置为**添加**。 通过添加重新连接到 Button 控件按钮事件处理程序`Click="button1_Click"`属性。 画布块应如下所示：  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>自定义构造函数  
  
1.  在 TodoWindowControl.xaml.cs 文件中，添加以下 using 语句：  
  
    ```csharp  
    using System;  
    ```  
  
2.  添加对 TodoWindow 的公共引用并具有采用 TodoWindow 参数 TodoWindowControl 构造函数。 代码应如下所示：  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  在 TodoWindow.cs，更改 TodoWindowControl 构造函数，以包含 TodoWindow 参数。 代码应如下所示：  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>创建选项页  
 你可以提供中的页**选项**对话框中，以便用户可以更改工具窗口的设置。 创建选项页需要这两个类，用于描述的选项以及 TodoListPackage.cs 或 TodoListPackage.vb 文件中的条目。  
  
1.  添加一个名为类`ToolsOptions.cs`。 使 ToolsOptions 类继承自<xref:Microsoft.VisualStudio.Shell.DialogPage>。  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  添加以下 using 语句：  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  在本演练中的选项页提供了名为 DaysAhead 只有一个选项。 添加名为的私有字段**daysAhead**和一个名为属性**DaysAhead**到 ToolsOptions 类：  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 现在必须使该项目注意该选项页。  
  
#### <a name="make-the-options-page-available-to-users"></a>向用户提供选项页  
  
1.  在 TodoWindowPackage.cs，添加<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>到 TodoWindowPackage 类：  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  ProvideOptionPage 构造函数的第一个参数是类 ToolsOptions，先前创建的类型。 第二个参数，"ToDo"是中的类别的名称**选项**对话框。 第三个参数，"常规"，是的子类别的名称**选项**选项页将在其中可用的对话框。 下面的两个参数是用于字符串; 尝试添加的资源 Id第一个是具有类别的名称，第二个是子类别的名称。 最后一个参数确定是否可以通过使用自动化访问此页。  
  
     当用户打开选项页上时，它应类似于下图。  
  
     ![选项页](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     请注意类别**ToDo**和子类别**常规**。  
  
## <a name="make-data-available-to-the-properties-window"></a>使数据可用于属性窗口  
 可以通过创建一个名为 ToDo 列表中存储的各个项有关的信息的 TodoItem 类，请为列表信息可用。  
  
1.  添加一个名为类`TodoItem.cs`。  
  
     可供用户工具窗口时，将由 TodoItems 表示列表框中的项。 当用户选择其中一项在列表框中，**属性**窗口将显示有关项目的信息。  
  
     若要使数据中可用**属性**窗口中，你将数据转换为具有两个的特殊属性的公共属性`Description`和`Category`。 `Description`是的底部将显示的文本**属性**窗口。 `Category`确定属性应显示时**属性**窗口显示在**按分类顺序**视图。 在下面的图中，**属性**窗口处于**按分类顺序**视图中，**名称**中的属性**ToDo 字段**类别选择，和的描述**名称**属性显示在窗口的底部。  
  
     ![属性窗口](../extensibility/media/t5properties.png "T5Properties")  
  
2.  添加以下 using 语句 TodoItem.cs 文件。  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  添加`public`向类声明的访问修饰符。  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     添加两个属性名称和 DueDate。 我们将更高版本执行的 UpdateList() 和 CheckForErrors()。  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  添加到用户控件的专用引用。 添加的构造函数的用户控件并将此 ToDo 项的名称。 若要查找 daysAhead 值，它获取选项页属性。  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  因为的实例`TodoItem`类将存储在列表框和列表框将调用`ToString`函数，您必须重载`ToString`函数。 构造函数之后和类的末尾之前，请将以下代码添加到 TodoItem.cs。  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  在 TodoWindowControl.xaml.cs，将存根 （stub） 方法添加到的 TodoWindowControl 类`CheckForError`和`UpdateList`方法。 之后 ProcessDialogChar 和文件的末尾之前将它们放置。  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`方法将调用程序中父对象，具有相同名称的方法，该方法将检查是否已发生的任何错误，并正确处理它们。 `UpdateList`方法将更新在父控件中的列表框; 当调用该方法`Name`和`DueDate`中此类更改的属性。 它们将更高版本实现。  
  
## <a name="integrate-into-the-properties-window"></a>将集成到属性窗口  
 现在编写管理列表框，将绑定到的代码**属性**窗口。  
  
 必须更改按钮单击处理程序以读取文本框中，创建 TodoItem，并将其添加到列表框。  
  
1.  将现有`button1_Click`创建新的 TodoItem 并将其添加到列表框的代码的函数。 它调用 TrackSelection()，将在以后定义。  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  在设计视图选择列表框控件。 在**属性**窗口中，单击**事件处理程序**按钮并找到 SelectionChanged 事件。 在文本框中填充**listBox_SelectionChanged**。 执行此操作将添加存根出于 SelectionChanged 处理程序，并将其分配给该事件。  
  
3.  实现 TrackSelection() 方法。 因为您将需要它来获取<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell><xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服务，你需要做<xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>TodoWindowControl 可访问。 将以下方法添加到 TodoWindow 类：  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  添加以下 using 语句 TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  填充 SelectionChanged 处理程序中，如下所示：  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  现在，填充在 TrackSelection 函数中，将提供与集成**属性**窗口。 用户将某项添加到列表框，或单击列表框中的项时调用此函数。 它将列表框的内容添加到 SelectionContainer 并将传递到 SelectionContainer**属性**窗口<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>事件处理程序。 TrackSelection 服务跟踪的用户界面 (UI) 中的所选的对象，并显示其属性  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     现在，你有了一个类，**属性**窗口可以使用，您可以将集成**属性**与工具窗口的窗口。 当用户单击工具窗口中，在列表框中的项**属性**窗口应相应地更新。 同样，当用户更改中的 ToDo 项**属性**窗口中，应更新关联的项。  
  
7.  现在，在 TodoWindowControl.xaml.cs 添加 UpdateList 函数代码的其余部分。 它应删除并重新从列表框中添加已修改的 TodoItem。  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  测试你的代码。 生成项目并启动调试。 应显示的实验实例。  
  
9. 打开**工具 / 选项**页。 你应看到在左窗格中的 ToDo 类别。 按字母顺序列出了类别中，因此在 Ts 下查找。  
  
10. 在 Todo 选项页中，你会看到 DaysAhead 属性设置为**0**。 将其更改为**2**。  
  
11. 对视图 / 其他窗口菜单上，打开**TodoWindow**。 类型**EndDate**在文本框中单击**添加**。  
  
12. 在列表框中，你应看到两个天晚于今天的日期。  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>将文本添加到输出窗口中，然后向任务列表项  
 有关**任务列表**，创建的类型任务中，一个新对象，然后该任务将对象添加到**任务列表**通过调用其 Add 方法。 要写入到**输出**窗口中，调用以获取窗格对象，其 GetPane 方法，然后你调用窗格中对象的 OutputString 方法。  
  
1.  在 TodoWindowControl.xaml.cs，在`button1_Click`方法，添加代码以获取**常规**窗格**输出**窗口中 （这是默认值），并向其中写入。 该方法应如下所示：  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  若要将项添加到任务列表中，你需要将嵌套的类添加到 TodoWindowControl 类。 嵌套的类必须派生自<xref:Microsoft.VisualStudio.Shell.TaskProvider>。 将以下代码添加到 TodoWindowControl 类的末尾。  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  接下来将对 TodoTaskProvider 的私有引用和 CreateProvider() 方法添加到 TodoWindowControl 类。 代码应如下所示：  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  将 ClearError()，清除任务列表和 ReportError()，将条目添加到任务列表中，添加到 TodoWindowControl 类。  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  现在，如下所示实现 CheckForErrors 方法。  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>为了试验  
  
1.  生成项目并启动调试。 实验实例中出现。  
  
2.  打开 TodoWindow (**视图 / 其他 Windows / TodoWindow**)。  
  
3.  在文本框中键入内容，然后单击**添加**。  
  
     截止日期后今天被添加到列表中的 2 天。 未出现任何错误，与**任务列表**(**查看 / 任务列表**) 应没有任何条目。  
  
4.  现在将设置更改启用**工具 / 选项 / ToDo**来自页**2**回**0**。  
  
5.  键入内容中的其他**TodoWindow** ，然后单击**添加**试。 这会触发错误以及将项记入**任务列表**。  
  
     当添加项时，初始的日期设置为现在再加上 2 天。  
  
6.  上**视图**菜单上，单击**输出**以打开**输出**窗口。  
  
     请注意，每次将某个项，在显示一条消息**任务列表**窗格。  
  
7.  单击其中一个列表框中的项。  
  
     **属性**窗口显示两个项的属性。  
  
8.  更改属性之一，然后按 enter 键。  
  
     在列表框中更新项目。
