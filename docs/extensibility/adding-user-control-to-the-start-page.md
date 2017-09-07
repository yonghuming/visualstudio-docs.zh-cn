---
title: "将用户控件添加到开始页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 16
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
ms.openlocfilehash: ed511fa58ca0d98d38ed2ab1ed3bc24bed642170
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="adding-user-control-to-the-start-page"></a>将用户控件添加到开始页
本演练演示如何添加对自定义起始页的 DLL 引用。 该示例添加到解决方案中，用户控件生成用户控件，并从起始页.xaml 文件然后引用生成的程序集。 一个新选项卡承载用户控件，用作基本 Web 浏览器。  
  
 可以使用相同的过程将从.xaml 文件可以调用任何程序集添加。  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>将 WPF 用户控件添加到解决方案  
 首先，将 Windows Presentation Foundation (WPF) 用户控件添加到起始页解决方案。  
  
1.  创建起始页通过使用我们在中创建[创建自定义起始页](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在**解决方案资源管理器**，右键单击该解决方案，单击**添加**，然后单击**新项目**。  
  
3.  在左窗格中**新项目**对话框框中，展开**Visual Basic**或**Visual C#**节点，然后单击**Windows**。 在中间窗格中，选择**WPF 用户控件库**。  
  
4.  命名该控件`WebUserControl`，然后单击**确定**。  
  
## <a name="implementing-the-user-control"></a>实现用户控件  
 若要实现 WPF 用户控件，生成在 XAML 中的用户界面 (UI)，然后在 C# 或其他.NET 语言编写的代码隐藏事件。  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>若要编写的 XAML 用户控件  
  
1.  打开用户控件的 XAML 文件。 在\<网格 > 元素，将以下行定义添加到控件。  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  在 main 中`Grid`元素中，添加以下新`Grid`元素，它包含用于键入 Web 地址和一个用于设置的新地址按钮的文本框。  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  将以下帧添加到顶级`Grid`元素紧后面`Grid`包含按钮和文本框中的元素。  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  下面的示例显示已完成的 XAML 用户控件。  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>若要编写用户控件的代码隐藏事件  
  
1.  在 XAML 设计器中，双击**设置地址**按钮添加到控件。  
  
     UserControl1.cs 文件将在代码编辑器中打开。  
  
2.  如下所示填写 SetButton_Click 事件处理程序。  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     此代码将设置作为 Web 浏览器的目标在文本框中键入 Web 地址。 如果的地址不是有效的则代码将引发错误。  
  
3.  你还必须处理 WebFrame_Navigated 事件：  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  生成解决方案。  
  
## <a name="adding-the-user-control-to-the-start-page"></a>将用户控件添加到开始页  
 若要使此控件可用于的起始页项目，起始页项目文件中，添加对新的控件库的引用。 然后你可以将控件添加到起始页 XAML 标记中。  
  
1.  在**解决方案资源管理器**，在起始页项目中，右键单击**引用**，然后单击**添加引用**。  
  
2.  上**项目**选项卡上，选择**WebUserControl** ，然后单击**确定**。  
  
3.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     生成解决方案使用户控制可向 IntelliSense 的解决方案中其他文件。  
  
 若要将控件添加到起始页 XAML 标记中，添加对程序集的命名空间引用，然后将页上的控件。  
  
#### <a name="to-add-the-control-to-the-markup"></a>若要将控件添加到标记  
  
1.  在**解决方案资源管理器**，打开起始页.xaml 文件。  
  
2.  在**XAML**窗格中，将以下命名空间声明添加到顶级<xref:System.Windows.Controls.Grid>元素。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  在**XAML**窗格中，滚动到\<网格 > 部分。  
  
     部分包含<xref:System.Windows.Controls.TabControl>中的元素<xref:System.Windows.Controls.Grid>元素。  
  
4.  添加\<TabControl > 元素，其中包含\<TabItem >，其中包含对你的用户控件的引用。  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 现在，你可以测试控件。  
  
## <a name="testing-a-manually-created-custom-start-page"></a>测试手动创建自定义起始页  
  
1.  将你的 XAML 文件，以及任何支持的文本文件或标记文件，为复制**%USERPROFILE%\My Documents\Visual Studio 2015 \startpages\\** 文件夹。  
  
2.  如果你的起始页引用的任何控件或未安装 Visual studio 的程序集中的类型，复制程序集，然后粘贴在*Visual Studio 安装文件夹***\Common7\IDE\PrivateAssemblies\\**。  
  
3.  在 Visual Studio 命令提示符处，键入**devenv /rootsuffix Exp**若要打开 Visual Studio 的实验实例。  
  
4.  在实验实例中，转到**工具 / 选项 / 环境 / 启动**页，选择你的 XAML 文件从**自定义起始页**下拉列表。  
  
5.  在“视图”  菜单上，单击“起始页” 。  
  
     应显示你的自定义起始页。 如果你想要更改的任何文件，你必须关闭实验实例，进行更改、 复制和粘贴已更改的文件，以及然后重新打开实验实例，以查看所做的更改。  
  
## <a name="see-also"></a>另请参阅  
 [WPF 容器控件](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [演练：将自定义 XAML 添加到起始页](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
