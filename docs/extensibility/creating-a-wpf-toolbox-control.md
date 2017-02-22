---
title: "创建 WPF 工具箱控件 | Microsoft Docs"
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
  - "在工具箱控件"
  - "工具箱"
  - "wpf"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 创建 WPF 工具箱控件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

WPF \(Windows Presentation Framework\) 工具箱控件模板允许您创建 WPF 控件，会自动添加到 **工具箱** 安装扩展的安装。 本主题演示如何使用模板来创建 **工具箱** 可以分发给其他用户的控件。  
  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 WPF 工具箱控件  
  
#### 与 WPF 工具箱控件中创建的扩展  
  
1.  创建一个名为的 VSIX 项目 `MyToolboxControl`。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\# \/ 可扩展性**。  
  
2.  在打开该项目，添加 **WPF 工具箱控件** 项模板名为 `MyToolboxControl`。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **WPF 工具箱控件**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 `MyToolboxControl.cs`。  
  
     该解决方案现在包含一个用户控件， `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，将控件添加到 **工具箱**, ，和一个 **Microsoft.VisualStudio.ToolboxControl** 资产部署的 VSIX 清单中的条目。  
  
#### 若要创建控件用户界面  
  
1.  在设计器中打开 MyToolboxControl.xaml。  
  
     此设计器显示包含 <xref:System.Windows.Controls.Button> 控件的 <xref:System.Windows.Controls.Grid> 控件。  
  
2.  排列网格布局。 当您选择 <xref:System.Windows.Controls.Grid> 控制，网格的顶部和左侧边缘上显示蓝色的控件条。 您可以添加到网格的行和列，方法是单击标题栏。  
  
3.  将子控件添加到网格。 您可以通过将其从拖动定位子控件 **工具箱** 部分的网格中，或通过设置其 `Grid.Row` 和 `Grid.Column` 在 XAML 中的属性。 下面的示例在网格中，然后第二行上的按钮的顶行上添加两个标签。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## 重命名控件  
 默认情况下，您的控件将出现在 **工具箱** 作为 **MyToolboxControl** 中一个名为组 **MyToolboxControl.MyToolboxControl**。 您可以更改这些名称 MyToolboxControl.xaml.cs 文件中。  
  
1.  在代码视图中打开 MyToolboxControl.xaml.cs。  
  
2.  查找 MyToolboxControl 类并将它重命名为 TestControl。 \(若要这样做的最快方法是重命名类中，然后选择 **重命名** 从上下文菜单并完成的步骤。 \(有关详细信息 **重命名** 命令，请参阅 [重命名重构 \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)。\)  
  
3.  转到 `ProvideToolboxControl` 属性并更改的第一个参数的值 **测试**。 这是将包含控件中的组的名称 **工具箱**。  
  
     生成的代码应如下所示︰  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## 生成、测试和部署  
 当调试项目时，您应会看到在安装该控件 **工具箱** 的 Visual Studio 的实验实例。  
  
#### 生成并测试控件  
  
1.  重新生成项目并启动调试。  
  
2.  在 Visual Studio 的新实例中，创建 WPF 应用程序项目。 请确保 XAML 设计器处于打开状态。  
  
3.  在“工具箱”中查找控件，并将其拖动到设计图面上。  
  
4.  开始调试 WPF 应用程序。  
  
5.  确认出现了您的控件。  
  
#### 部署控件  
  
1.  生成测试的项目后，可以在项目的 \\bin\\debug\\ 文件夹中找到的.vsix 文件。  
  
2.  您可以安装它在本地计算机上双击.vsix 文件并按照安装过程。 若要卸载该控件，请转到 **工具 \/ 扩展和更新** 并寻找控件扩展，然后单击 **卸载**。  
  
3.  将 .vsix 文件上载到网络或网站。  
  
     如果您将文件上载到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847) 网站，其他用户可以使用 **工具 \/ 扩展和更新** 在 Visual Studio 中查找联机的控件并将其安装。