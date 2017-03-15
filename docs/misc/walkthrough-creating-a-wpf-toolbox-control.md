---
title: "演练：创建 WPF 工具箱控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱"
  - "wpf"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 演练：创建 WPF 工具箱控件
Visual Studio SDK 包含的 WPF 工具箱控件模板允许你创建 Windows Presentation Foundation \(WPF\) 控件，此控件会在安装扩展后自动添加到“工具箱”。 本演练演示如何使用模板创建可分发给其他用户的计数器控件。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关更多信息，请参见[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 在 Visual Studio 中查找 WPF 工具箱控件模板  
 WPF 工具箱控件模板在“新建项目”对话框中“已安装模板”下的以下位置可用：  
  
-   **Visual Basic**，“扩展性”。 项目的语言是 Visual Basic。  
  
-   **Visual C\#**，“扩展性”。 项目的语言是 C\#。  
  
## 创建 WPF 工具箱控件项目  
 WPF 工具箱控件模板可创建未定义的用户控件，并提供了将控件添加到“工具箱”所需的全部功能。  
  
#### 要创建项目  
  
1.  在**“文件”**菜单上，单击**“新建”**，然后单击**“项目”**。  
  
2.  在“新建项目”对话框的“已安装模板”下，单击首选编程语言的节点，然后选择“扩展性”。 在项目类型列表中，选择“WPF 工具箱控件”。  
  
3.  在“名称”框中，键入想要用于项目的名称。 （本演练使用名称 `Counter`。） 单击“确定”。  
  
     这将创建一个解决方案，内含用户控件、将控件置于“工具箱”中的特性，以及用于部署 VSIX 的清单。 “名称”框可设置解决方案的名称和命名空间的名称，但不设置“工具箱”中显示的控件的名称。 你将在本演练稍后部分中设置它。  
  
### 构建控件的用户界面  
 `Counter` 控件需要 3 个子控件：2 个显示文本的 <xref:System.Windows.Controls.Label> 控件、当前计数，及 1 个将计数重置为 0 的 <xref:System.Windows.Controls.Button> 控件。 不需要其他子控件，因为托管应用程序将以编程方式递增计数器。  
  
##### 构建用户界面  
  
1.  在“解决方案资源管理器”中双击 ToolboxControl.cs，以在设计器中打开它。  
  
     此设计器显示包含 <xref:System.Windows.Controls.Button> 控件的 <xref:System.Windows.Controls.Grid> 控件。  
  
2.  选择 <xref:System.Windows.Controls.Grid> 控件，然后单击网格顶部和左侧出现的蓝色条，将其划分为两行两列。  
  
3.  从“工具箱”中，将 <xref:System.Windows.Controls.Label> 控件拖动到网格首行的各单元格。  
  
     此时，你可以通过排列网格上的元素来设置控件的布局。 相反，你可以直接编辑可扩展应用程序标记语言 \(XAML\)，以便该控件动态调整大小以适合文本。  
  
4.  在“XAML”窗格中，将`RowDefinition` 元素的高度和 `ColumnDefinition` 元素的宽度设置为 `"auto"`。  
  
5.  编辑用于按钮和两个标签的标记，类似于以下示例。  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     `Grid.Row` 和 `Grid.Column` 特性可设置元素在网格上的位置。 按钮上的 `Grid.ColumnSpan` 特性使首列可以自行调整大小，而不管按钮的宽度。  
  
     标签的 `Content` 特性使用 `{Binding}` 语法以绑定到将在本演练稍后部分中定义的特性。  
  
### 编码用户控件  
 `Counter` 控件将公开一个用于递增计数器的方法、一个计数器每次递增时均会引发的事件、一个 `Reset` 按钮，以及 3 个存储当前计数、显示文本及是显示还是隐藏 `Reset` 按钮的属性。`ProvideTolboxControl` 特性确定 `Counter` 控件会出现在“工具箱”的什么位置。  
  
 可以按编写 Windows 窗体控件相同的方式编写此控件，即通过使用事件处理程序和公共方法设置标签的内容。 但是，可以在 WPF 中设置该控件的数据上下文，以便可以将 XAML 元素特性直接绑定到代码中的特性。 此模型还提供了一个抽象层，用于从控件的用户界面 \(UI\) 中分离核心功能。  
  
 本演练演示如何创建数据模型类，然后如何将控件的数据上下文绑定到数据模型。  
  
##### 创建数据模型  
  
1.  双击按钮以打开代码窗口。  
  
2.  在文件顶部，为 <xref:System.ComponentModel> 命名空间添加 `using` 指令。  
  
3.  在生成类后，创建一个公共类以定义数据上下文。  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     此类实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口，可将 XAML 元素绑定到已定义的属性。  
  
4.  右键单击 <xref:System.ComponentModel.INotifyPropertyChanged> 接口声明，单击“实现接口”，然后再次单击“实现接口”。  
  
     Visual Studio 声明 `PropertyChanged` 事件。  
  
5.  事件声明后，创建以下私有方法来引发此事件。  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  创建下列私有字段和公共属性，以在控件中保存两个标签的值。  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     引发 `PropertyChanged` 事件会导致 XAML 绑定更新绑定控件的内容。 设置属性为 `public` 可使它们在设计器中可用，但对其他程序不可用（除非其绑定到此数据上下文）。  
  
 由于已创建数据模型，你可以实现此控件的代码隐藏功能。  
  
##### 实现控件  
  
1.  在实现控件的部分类定义处，右键单击类名称，单击“重构”，再单击“重命名”，然后将类名改为 `Counter`。 安装扩展后，这就是将在“工具箱”中显示的名称。  
  
2.  在类定义正上方的 `ProvideToolboxControl` 特性声明中，将第一个参数的值从 `"Counter"` 改为 `"General"`。 这会设置将在“工具箱”中托管控件的项组名称。  
  
     以下示例演示了 `ProvideToolboxControl` 特性和调整后的类定义。  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  创建私有字段以托管控件的数据上下文，然后在构造函数中将数据上下文分配给 `MyDataModel` 类，如下方示例所示。  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  创建下列公共属性以映射数据上下文中的 `Text` 和 `Count` 属性。  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     这些属性使数据上下文的内容可用于包含控件的任何应用程序。  
  
5.  创建下列可递增计数器的公共方法，以及一个用于通知托管应用程序的事件。  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  为 `Reset` 按钮实现单击处理程序，如下所示。  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  添加以下公共属性，以显示或隐藏 `Reset` 按钮。  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## 测试控件  
 若要测试“工具箱”控件，请先在开发环境中测试它，然后在托管应用程序中进行测试。  
  
#### 测试控件  
  
1.  按 F5。  
  
     这将生成项目，并打开已安装此控件的 Visual Studio 的第二个实例。  
  
2.  在 Visual Studio 的新实例中，创建 WPF 应用程序项目。  
  
3.  在“解决方案资源管理器”中，双击 MainWindow.xaml 以在设计器中打开它。  
  
4.  从“工具箱”的“常规”部分，将“计数器”控件拖动到你的窗体，然后选中它。  
  
     `Text` 和 `ShowReset` 属性将与继承自 <xref:System.Windows.Controls.UserControl> 的其他属性一起显示在“属性”窗口中。 不会显示 `Count` 属性，因为它是只读的。  
  
5.  更改 `Text` 属性的值。  
  
     会更改设计器中显示的标签文本。  
  
6.  将 `ShowReset` 属性设置为 `Hidden`，然后将其设置回 `Visible`。  
  
     控件上的 `Reset` 按钮将消失，然后再次出现。  
  
7.  将 <xref:System.Windows.Controls.Button> 控件拖动到窗体，将其 `Content``` 特性设置为 `Test`，然后双击此按钮以在代码视图中打开它的单击处理程序。  
  
8.  实现单击处理程序以调用控件的 `Increment` 方法。  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. 在构造函数中，在调用 `InitializeComponent` 后，键入 `counter1.Implemented +=`，然后按 Tab 键两次以生成 `Counter.Incremented` 事件的处理程序。  
  
10. 实现新的处理程序，如下例中所示。  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. 按 F5。  
  
     将打开 WPF 应用程序。  
  
12. 单击“测试”。  
  
     计数器将递增且按钮会稍微淡化。  
  
13. 再单击“测试”四次。  
  
     将递增此计数器，且按钮会继续淡化直至消失。 如果继续单击按钮，计数器将继续递增。  
  
14. 单击“重置”。  
  
     计数器将重置为“0”。  
  
## 后续步骤  
 生成“工具箱”控件时，Visual Studio 将在项目的 \\bin\\debug\\ 文件夹中创建一个名为 *项目名称* .vsix 的文件。 你可以通过将 .vsix 文件上载到网络或网站来部署此控件。 在用户打开.vsix 文件时，此控件得到安装，并添加到 Visual Studio“工具箱”。 或者，如果你将 .vsix 文件上载到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，则用户可在“扩展管理器”中浏览时找到它。  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [创建 Windows 窗体工具箱控件](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用 WPF 设计器中的控件](http://msdn.microsoft.com/zh-cn/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [控件创作概述](../Topic/Control%20Authoring%20Overview.md)