---
title: "公开属性设置为属性窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性浏览器中公开的属性 [Visual Studio SDK]"
  - "属性 [Visual Studio SDK]"
  - "属性浏览器中，公开属性"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 公开属性设置为属性窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练中公开某一对象的公共属性 **属性** 窗口。 对这些属性所做的更改反映在 **属性** 窗口。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 公开属性设置为属性窗口  
 在本部分中，可以创建一个自定义工具窗口和显示中的关联的窗口窗格中对象的公共属性 **属性** 窗口。  
  
#### 若要公开属性设置为属性窗口  
  
1.  每个 Visual Studio 的扩展从一个 VSIX 部署项目，它将包含的扩展资产开始。 创建 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 项目名为 `MyObjectPropertiesExtension`。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  通过添加一个名为的自定义工具窗口项模板添加一个工具窗口 `MyToolWindow`。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项对话框**, ，请转到 **Visual C\# 项 \/ 扩展性** ，然后选择 **自定义工具窗口**。 在 **名称** 在对话框底部字段中，文件将名称更改为 `MyToolWindow.cs`。 有关如何创建自定义工具窗口的详细信息，请参阅 [使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  打开 MyToolWindow.cs 并添加以下 using 语句:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  现在，添加以下字段写入 `MyToolWindow` 类。  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  将以下代码添加到 MyToolWindow 类。  
  
    ```c#  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` 属性使用 `GetService` 获取 `STrackSelection` 服务，它提供了 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 接口。`OnToolWindowCreated` 事件处理程序和 `SelectList` 方法共同创建所选对象的列表，其中包含仅将工具窗口窗格中的对象本身。`UpdateSelection` 方法会示意 **属性** 窗口以显示工具窗口窗格中的公共属性。  
  
6.  生成项目并启动调试。 Visual Studio 的实验实例应显示。  
  
7.  如果 **属性** 窗口不可见，请按 F4 打开。  
  
8.  打开 **MyToolWindow** 窗口。 你可以找到它在 **视图 \/ 其他窗口**。  
  
     将打开的窗口和窗口窗格中的公共属性显示在 **属性** 窗口。  
  
9. 更改 **标题** 中的属性 **属性** 窗口 **我的对象属性**。  
  
     MyToolWindow 窗口标题也会相应改变。  
  
## 公开工具窗口属性  
 在本部分中，可以添加一个工具窗口和公开其属性。 对属性所做的更改反映在 **属性** 窗口。  
  
#### 若要公开工具窗口属性  
  
1.  打开 MyToolWindow.cs，并将公共的布尔值属性 IsChecked 添加到 MyToolWindow 类。  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     此属性获取其状态从 WPF 复选框将在以后创建。  
  
2.  打开 MyToolWindowControl.xaml.cs 并替换为以下代码替换 MyToolWindowControl 构造函数。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     这使 `MyToolWindowControl` 访问 `MyToolWindow` 窗格。  
  
3.  在 MyToolWindow.cs，更改 `MyToolWindow` 构造函数，如下所示:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  将更改为 MyToolWindowControl 的设计视图。  
  
5.  删除按钮并添加一个复选框，从 **工具箱** 到左上角。  
  
6.  添加了选中和未选中事件。 在设计视图中选择该复选框。 在 **属性** 窗口中，单击事件处理程序按钮 \(顶部右侧的 **属性** 窗口\)。 查找 **Checked** 和类型 **checkbox\_Checked** 在文本框中，然后找到 **选中此项** 和类型 **checkbox\_Unchecked** 在文本框中。  
  
7.  添加复选框事件处理程序:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  生成项目并启动调试。  
  
9. 在实验实例中，打开 **MyToolWindow** 窗口。  
  
     中的窗口的属性查找 **属性** 窗口。**IsChecked** 属性下将出现在窗口的底部 **我属性** 类别。  
  
10. 选中该复选框 **MyToolWindow** 窗口。**IsChecked** 中 **属性** 窗口更改为 **True**。 清除该复选框在 **MyToolWindow** 窗口。**IsChecked** 中 **属性** 窗口更改为 **False**。 值更改 **IsChecked** 中 **属性** 窗口。 中的复选框 **MyToolWindow** 窗口更改为与新值匹配。  
  
    > [!NOTE]
    >  如果必须在显示的对象释放 **属性** 窗口中，调用 `OnSelectChange` 与 `null` 选择容器第一个。 后释放该属性或对象，您可以更改为已更新的选择容器 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> 和 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 列出。  
  
## 更改所选内容列表  
 在本部分中，可以添加基本属性类的选项列表和使用工具窗口界面选择要显示的选择列表。  
  
#### 若要更改的选择列表  
  
1.  打开 MyToolWindow.cs 并添加一个名为的公共类 `Simple`。  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  将 SimpleObject 属性添加到 MyToolWindow 类，还有两种方法来切换 **属性** 窗口窗格之间的窗口选择和 `Simple` 对象。  
  
    ```c#  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  在 MyToolWindowControl.cs，替换这些代码行的复选框处理程序:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  生成项目并启动调试。  
  
5.  在实验实例中，打开 **MyToolWindow** 窗口。  
  
6.  选中复选框在 **MyToolWindow** 窗口。**属性** 窗口显示 `Simple` 对象属性， **SomeText** 和 **ReadOnly**。 清除复选框。 窗口中的公共属性显示在 **属性** 窗口。  
  
    > [!NOTE]
    >  显示名称 **SomeText** 是 **我文本**。  
  
## 最佳做法  
 在本演练中， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 实现，因此可选择对象集合和所选的对象集合是相同的集合。 仅所选的对象显示在属性浏览器列表。 有关更完整的 ISelectionContainer 实现，请参阅 Reference.ToolWindow 示例。  
  
 Visual Studio 会话之间保留 visual Studio 工具窗口。 有关保留工具窗口状态的详细信息，请参阅 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## 请参阅  
 [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)