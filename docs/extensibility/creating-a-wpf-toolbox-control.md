---
title: "创建 WPF 工具箱控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 313f89f0fe9a4bf9e9171ebafc866366067ab98c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-wpf-toolbox-control"></a>创建 WPF 工具箱控件
(Windows Presentation Framework) WPF 工具箱控件模板允许您创建自动添加到的 WPF 控件**工具箱**安装扩展后。 本主题演示如何使用模板创建**工具箱**可以分发给其他用户控件。  
  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-wpf-toolbox-control"></a>创建 WPF 工具箱控件  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>使用 WPF 工具箱控件创建扩展  
  
1.  创建一个名为的 VSIX 项目`MyToolboxControl`。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  在打开该项目，添加**WPF 工具箱控件**项模板名为`MyToolboxControl`。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**WPF 工具箱控件**。 在**名称**在窗口底部字段中，命令文件名称更改为`MyToolboxControl.cs`。  
  
     解决方案现在包含一个用户控件， `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> ，它将添加到控件**工具箱**，和一个**Microsoft.VisualStudio.ToolboxControl**的 VSIX 清单中的资产条目 部署。  
  
#### <a name="to-create-the-control-ui"></a>若要创建控件 UI  
  
1.  在设计器中打开 MyToolboxControl.xaml。  
  
     此设计器显示<xref:System.Windows.Controls.Grid>包含控件<xref:System.Windows.Controls.Button>控件。  
  
2.  排列网格布局。 当选择<xref:System.Windows.Controls.Grid>控制，蓝色控件条显示在网格的边缘和左边缘。 你可以添加到网格的行和列，方法是单击标题栏。  
  
3.  将子控件添加到网格。 您可以通过拖动从定位子控件**工具箱**对分区的网格中，或通过设置其`Grid.Row`和`Grid.Column`在 XAML 中的属性。 下面的示例将两个标签添加网格和第二行上的按钮的最上面一行。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>重命名控件  
 默认情况下，控件将显示在**工具箱**作为**MyToolboxControl**中名为的组**MyToolboxControl.MyToolboxControl**。 你可以更改这些名称 MyToolboxControl.xaml.cs 文件中。  
  
1.  在代码视图中打开 MyToolboxControl.xaml.cs。  
  
2.  查找 MyToolboxControl 类并将它重命名为 TestControl。 (若要执行此操作的最快方法是重命名类，然后选择**重命名**从上下文菜单并完成步骤。 (有关详细信息**重命名**命令，请参阅[重命名重构 (C#)](../csharp-ide/rename-refactoring-csharp.md)。)  
  
3.  转到`ProvideToolboxControl`属性和更改的第一个参数的值**测试**。 这是将包含在控件组的名称**工具箱**。  
  
     生成的代码应如下所示：  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>生成、测试和部署  
 调试项目时，你应该看到在安装此控件**工具箱**的 Visual Studio 的实验实例。  
  
#### <a name="to-build-and-test-the-control"></a>生成并测试控件  
  
1.  重新生成项目并启动调试。  
  
2.  在 Visual Studio 的新实例中，创建 WPF 应用程序项目。 请确保 XAML 设计器处于打开状态。  
  
3.  在“工具箱”  中查找控件，并将其拖动到设计图面上。  
  
4.  开始调试 WPF 应用程序。  
  
5.  确认出现了您的控件。  
  
#### <a name="to-deploy-the-control"></a>部署控件  
  
1.  生成测试的项目后，你可以在项目的 \bin\debug\ 文件夹中找到.vsix 文件。  
  
2.  你可以安装它的本地计算机上通过双击.vsix 文件并按照安装过程。 若要卸载该控件，请转到**工具 / 扩展和更新**并查找控件扩展，然后单击**卸载**。  
  
3.  将 .vsix 文件上载到网络或网站。  
  
     如果你将文件上载到[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，可以使用其他用户**工具 / 扩展和更新**查找控件联机并将其安装的 Visual Studio 中。