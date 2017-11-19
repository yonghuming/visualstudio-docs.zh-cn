---
title: "演练： 在起始页上保存用户设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a7d8649e0d8cf83650da58386901e638ec14a2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>演练： 将用户设置保存在起始页上
为你的起始页，可以保留用户设置。 通过完成本演练，你可以创建将设置保存到注册表中，当用户单击按钮时，，然后检索，将设置的每次加载起始页的控件。 因为起始页项目模板包含一个可自定义用户控件，并且默认起始页 XAML 将调用该控件，你无需修改启动页本身。  
  
 在本演练中实例化的设置存储是的一个实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>接口，该读取和写入到以下注册表位置中，被调用时接口： HKCU\Software\Microsoft\VisualStudio\14.0\\ *CollectionName*  
  
 当 Visual Studio 的实验实例中运行时，设置存储读取和写入到 HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName。*  
  
 有关如何保存设置的详细信息，请参阅[扩展用户设置和选项](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>先决条件  
  
> [!NOTE]
>  要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
>   
>  你可以通过使用下载起始页项目模板**扩展管理器**。  
  
## <a name="setting-up-the-project"></a>设置项目  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>若要为本演练中配置项目  
  
1.  创建起始页项目中所述[创建自定义起始页](creating-a-custom-start-page.md)。 将项目**SaveMySettings**。  
  
2.  在**解决方案资源管理器**，添加对 StartPageControl 项目的以下程序集引用：  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  打开 MyControl.xaml。  
  
4.  从 XAML 窗格中，位于顶级<xref:System.Windows.Controls.UserControl>元素定义中，添加以下事件声明后的命名空间声明。  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  在设计窗格中，单击该控件的主要区域，然后按删除。  
  
     这将删除<xref:System.Windows.Controls.Border>元素和中，并使仅顶级的所有内容<xref:System.Windows.Controls.Grid>元素。  
  
6.  从**工具箱**，拖动<xref:System.Windows.Controls.StackPanel>控件添加到网格。  
  
7.  现在，将拖动<xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>，和一个按钮到<xref:System.Windows.Controls.StackPanel>。  
  
8.  添加**X:name**属性，则为<xref:System.Windows.Controls.TextBox>，和一个`Click`事件<xref:System.Windows.Controls.Button>，下面的示例中所示。  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>实现用户控件  
  
#### <a name="to-implement-the-user-control"></a>若要实现用户控件  
  
1.  在 XAML 窗格中，右键单击`Click`属性<xref:System.Windows.Controls.Button>元素，，然后单击**定位到事件处理程序**。  
  
     这将打开 MyControl.xaml.cs，并创建存根 （stub） 处理程序`Button_Click`事件。  
  
2.  添加以下`using`到文件顶部的语句。  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  添加一个私有`SettingsStore`属性，如下面的示例中所示。  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     此属性将首先获取对引用<xref:EnvDTE80.DTE2>接口，其中包含从自动化对象模型，<xref:System.Windows.FrameworkElement.DataContext%2A>的用户控件，然后使用以获取其实例对 DTE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>接口。 然后它使用该实例来返回当前用户设置。  
  
4.  填写`Button_Click`，如下所示的事件。  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     这将文本框的内容写入注册表中的"MySettings"集合中的"MySetting"字段中。 如果集合不存在，则创建它。  
  
5.  添加以下处理程序`OnLoaded`用户控件的事件。  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     这将文本框中的文本设置为"MySetting"的当前值。  
  
6.  生成用户控件。  
  
7.  在**解决方案资源管理器**，打开 source.extension.vsixmanifest。  
  
8.  在清单编辑器中，设置**产品名称**到**保存我的设置起始页**。  
  
     此设置的启动页的名称，因为它是显示在**自定义起始页**列入**选项**对话框。  
  
9. 生成 StartPage.xaml。  
  
## <a name="testing-the-control"></a>测试控件  
  
#### <a name="to-test-the-user-control"></a>若要测试该用户控件  
  
1.  按 F5。  
  
     此时将打开 Visual Studio 的实验实例。  
  
2.  在实验实例中，在**工具**菜单上，单击**选项**。  
  
3.  在**环境**节点，单击**启动**，然后在**自定义起始页**列表中，选择**[已安装的扩展] 保存我设置起始页**.  
  
     单击“确定”。  
  
4.  关闭处于打开状态，，然后，在启动页**视图**菜单上，单击**起始页**。  
  
5.  在启动页上，单击**MyControl**选项卡。  
  
6.  在文本框中，键入**Cat**，然后单击**保存我设置**。  
  
7.  关闭启动页，然后再次打开它。  
  
     在文本框中，应显示单词"Cat"。  
  
8.  将替换为"Dog"的单词的单词"Cat"。 请不要单击按钮。  
  
9. 关闭启动页，然后再次打开它。  
  
     在文本框中，应显示单词"Dog"，即使不保存设置。 这是因为 Visual Studio 将工具窗口保留在内存中，即使它们都将关闭，直到关闭 Visual Studio 自身。  
  
10. 关闭 Visual Studio 的实验实例。  
  
11. 按 f5 键以重新打开实验实例。  
  
12. 在文本框中，应显示单词"Cat"。  
  
## <a name="next-steps"></a>后续步骤  
 你可以修改此用户控制选项可保存和检索通过使用从不同的事件处理程序的不同值获取和设置的任意数量的自定义设置`SettingsStore`属性。 只要你使用不同`propertyName`每次调用的参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>，值将不会覆盖彼此的注册表中。  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [将 Visual Studio 命令添加到起始页](../extensibility/adding-visual-studio-commands-to-a-start-page.md)