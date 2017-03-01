---
title: "演练︰ 将用户设置保存在起始页上 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>演练︰ 将用户设置保存在起始页上
您可以保留用户设置起始页。 通过遵循本演练，您可以创建将设置保存到注册表中，当用户单击按钮时，并随后检索，将设置的每次启动页将加载的控件。 因为起始页项目模板包括可自定义用户控件，并且默认起始页 XAML 将调用该控件，您无需修改启动页本身。  
  
 在本演练中实例化的设置存储区是实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>接口，它读取和写入到以下注册表位置被调用时︰ HKCU\Software\Microsoft\VisualStudio\14.0\\*CollectionName* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 当 Visual Studio 的实验实例中运行时，设置存储读取和写入到 HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*集合名称。*  
  
 有关如何保存设置的详细信息，请参阅[扩展用户设置和选项](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>先决条件  
  
> [!NOTE]
>  要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
>   
>  您可以通过使用下载起始页项目模板**扩展管理器**。  
  
## <a name="setting-up-the-project"></a>设置项目  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>若要为本演练中配置项目  
  
1.  创建起始页项目中所述[创建自定义起始页](creating-a-custom-start-page.md)。 将项目命名为**SaveMySettings**。  
  
2.  在**解决方案资源管理器**，添加以下程序集引用到 StartPageControl 项目︰  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  打开 MyControl.xaml。  
  
4.  从 XAML 窗格中的顶级<xref:System.Windows.Controls.UserControl>元素定义，添加以下命名空间声明后的事件声明。</xref:System.Windows.Controls.UserControl>  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  在设计窗格中，单击该控件的主要区域，然后按 DELETE。  
  
     此命令将删除<xref:System.Windows.Controls.Border>元素和所有内容，并使只有顶级<xref:System.Windows.Controls.Grid>元素。</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.Border>  
  
6.  从**工具箱**，拖动<xref:System.Windows.Controls.StackPanel>到网格控件。</xref:System.Windows.Controls.StackPanel>  
  
7.  现在，将拖动<xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>，和一个按钮到<xref:System.Windows.Controls.StackPanel>。</xref:System.Windows.Controls.StackPanel> </xref:System.Windows.Controls.TextBox> </xref:System.Windows.Controls.TextBlock>  
  
8.  添加**X:name**属性<xref:System.Windows.Controls.TextBox>，和一个`Click`事件<xref:System.Windows.Controls.Button>，如在下面的示例所示。</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox>  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>实现该用户控件  
  
#### <a name="to-implement-the-user-control"></a>若要实现用户控件  
  
1.  在 XAML 窗格中，右键单击`Click`属性<xref:System.Windows.Controls.Button>元素，然后单击**定位到事件处理程序**。</xref:System.Windows.Controls.Button>  
  
     此时将打开 MyControl.xaml.cs，并创建一个存根 （stub） 处理程序`Button_Click`事件。  
  
2.  将以下代码添加`using`语句的文件的顶部。  
  
     [!code-cs[StartPageDTE #&11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  添加一个私有`SettingsStore`属性，如下面的示例中所示。  
  
    ```c#  
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
  
     此属性首先获取对<xref:EnvDTE80.DTE2>接口，其中包含自动化对象模型中，从<xref:System.Windows.FrameworkElement.DataContext%2A>的用户控件，然后使用要获取其实例对 DTE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:System.Windows.FrameworkElement.DataContext%2A> </xref:EnvDTE80.DTE2> 然后它使用该实例将返回当前用户设置。  
  
4.  填写`Button_Click`，如下所示的事件。  
  
    ```c#  
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
  
     这将写入注册表中的"Mysetting"集合中的"MySetting"字段的文本框中的内容。 如果集合不存在，则创建它。  
  
5.  添加以下处理程序`OnLoaded`用户控件的事件。  
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     这将文本框中的文本设置为"MySetting"的当前值。  
  
6.  构建用户控件。  
  
7.  在**解决方案资源管理器**，打开 source.extension.vsixmanifest。  
  
8.  在清单编辑器中，设置**产品名称**到**保存我的设置起始页**。  
  
     这会将设置启动页的名称按原样出现在**自定义起始页**列入**选项**对话框。  
  
9. 生成 StartPage.xaml。  
  
## <a name="testing-the-control"></a>测试控件  
  
#### <a name="to-test-the-user-control"></a>若要测试的用户控件  
  
1.  按 F5。  
  
     打开 Visual Studio 的实验实例。  
  
2.  在实验实例中，在**工具**菜单上，单击**选项**。  
  
3.  在**环境**节点中，单击**启动**，然后在**自定义起始页**列表中，选择**[安装扩展] 保存我设置起始页**。  
  
     单击“确定”。  
  
4.  关闭已打开，，然后在启动页**视图**菜单上，单击**起始页**。  
  
5.  在启动页上，单击**MyControl**选项卡。  
  
6.  在文本框中，键入**Cat**，然后单击**保存我设置**。  
  
7.  关闭启动页，然后再次打开它。  
  
     应在文本框中显示单词"Cat"。  
  
8.  将替换为单词"Dog"word"Cat"。 请不要单击按钮。  
  
9. 关闭启动页，然后再次打开它。  
  
     在文本框中应显示单词"Dog"，即使不保存设置。 这是因为 Visual Studio 会工具窗口保留在内存中，即使它们都将关闭，直到关闭 Visual Studio 本身。  
  
10. 关闭 Visual Studio 的实验实例。  
  
11. 按 f5 键以重新打开的实验实例。  
  
12. 应在文本框中显示单词"Cat"。  
  
## <a name="next-steps"></a>后续步骤  
 您可以修改此用户控件能够保存和检索任意数量的自定义设置通过使用来自不同的事件处理程序的不同值来获取和设置`SettingsStore`属性。 只要您使用不同`propertyName`每次调用的参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>，值将不会覆盖另一个在注册表中。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>  
  
## <a name="see-also"></a>另请参阅  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [将 Visual Studio 命令添加到起始页](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
