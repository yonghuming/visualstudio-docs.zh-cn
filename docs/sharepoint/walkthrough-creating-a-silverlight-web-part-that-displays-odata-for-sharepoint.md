---
title: "演练：创建显示 SharePoint OData 的 Silverlight Web 部件"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 演练：创建显示 SharePoint OData 的 Silverlight Web 部件
  SharePoint 2010 通过 OData 公开其数据列表。  在 SharePoint 中，OData 服务由RESTful服务 ListData.svc 实现。  本演练演示如何创建此 SharePoint Web 部件承载的 Silverlight 应用程序。  使用 ListData.svc 的 Silverlight 应用程序信息显示 SharePoint 公告列表。  有关更多信息，请参见 [SharePoint Foundation 其他接口](http://go.microsoft.com/fwlink/?LinkId=225999) 和 [打开式数据协议](http://go.microsoft.com/fwlink/?LinkId=226000)。  
  
 本演练将演示以下任务：  
  
-   [创建 Silverlight 应用程序和 Silverlight Web 部件](#BKMK_creatingSLApp)。  
  
-   [自定义 Silverlight应用程序](#BKMK_customizeSLApp)。  
  
-   [自定义 Silverlight应用程序](#BKMK_customizeSLApp)。  
  
-   [自定义 Silverlight应用程序](#BKMK_customizeSLApp)。  
  
-   [测试 Silverlight Web 部件](#BKMK_testSLApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> 创建 Silverlight 应用程序和 Silverlight Web 部件  
 首先，请在 Visual Studio 中创建 Silverlight 应用程序。  通过使用 ListData.svc 服务，Silverlight 应用程序从SharePoint 公告列表中检索数据。  
  
> [!NOTE]  
>  在 4.0 支持需要的接口引用 SharePoint 列表数据之前，Silverlight 未生成。  
  
#### 创建 Silverlight 应用程序和 Silverlight Web 部件  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**，以显示**“新建项目”**对话框。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
3.  在"模板"窗格中，选择 **SharePoint 2010 Silverlight Web 部件** 模板。  
  
4.  在**“名称”**框中，输入 SLWebPartTest ，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**对话框。  
  
5.  在**“指定用于调试的网站和安全级别”**页上，输入要在其中调试网站定义的 SharePoint Server 网站的 URL，或者使用默认位置 \(http:\/\/*system name*\/\)。  
  
6.  在“此 SharePoint 解决方案的信任级别是什么?”部分中，选中“部署为场解决方案”选项按钮。  
  
     虽然此示例使用一个场解决方案，但 Silverlight Web 部件项目可以部署为场或沙盒解决方案。  有关沙盒化解决方案与场解决方案的更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在 **您希望以何种方式关联 Silverlight Web 部件** 部分 **指定 Silverlight 配置信息** 页中，选择 **新建一个 Silverlight 项目并将其与 Web 部件相关联** 选项按钮。  
  
8.  将 **名称** 更改为 SLApplication，将 **语言** 设置为 **Visual Basic** 或 **Visual C\#**，然后将 **Silverlight 版本** 设置为 **Silverlight 4.0**。  
  
9. 选择**“完成”**按钮。  该项目将显示在**“解决方案资源管理器”**中。  
  
     解决方案包含两个项目：Silverlight 应用程序和 Silverlight Web 部件。  Silverlight 应用程序检索并显示从 SharePoint 中的列表和 Silverlight 数据 Web 部件承载的 Silverlight 应用程序，使您能够在 SharePoint 中查阅。  
  
##  <a name="BKMK_customizeSLApp"></a> 自定义 Silverlight应用程序  
 添加代码和设计元素到 Silverlight 应用程序中。  
  
#### 自定义 Silverlight 应用程序：  
  
1.  在 Silverlight 应用程序中，向 System.Windows.Data 添加程序集引用。  有关详细信息，请参阅[如何：使用“添加引用”对话框添加或移除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
2.  在**“解决方案资源管理器”**中，打开**“引用”**的快捷菜单，然后选择**“添加服务引用”**。  
  
    > [!NOTE]  
    >  如果您使用的是 Visual Basic，则必须选择 **显示所有文件** 图标，在 **解决方案资源管理器** 顶部显示 **引用** 节点。  
  
3.  在地址框 **添加服务引用** 对话框中，输入 SharePoint 网站的 URL，如 **http:\/\/MySPSite**，然后选择 **转到** 按钮。  
  
     在 Silverlight ListData.svc 找到 SharePoint OData 服务时，则使用 URL 全服务替换地址。  对于此示例，http:\/\/myserver 成为 http:\/\/myserver\/\_vti\_bin\/ListData.svc。  
  
4.  选择 **确定** 按钮将服务引用添加到项目，并使用默认名称，ServiceReference1 服务。  
  
5.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
6.  添加基于 SharePoint 服务的新数据源。  为此，在菜单栏上，依次选择 **视图**，**其他窗口**，**数据源**。  
  
     **数据源** 窗口显示所有可用的 SharePoint 列表的数据 ，如任务、公告和日历。  
  
7.  添加公告列表数据到 Silverlight 应用程序。  您可以从 **数据源** 窗口拖动“公告”到 Silverlight 设计器上。  
  
     这将创建网格控件绑定到 SharePoint 网站的公告列表。  
  
8.  调整网格控件以适应 Silverlight 页。  
  
9. 在MainPage.xam代码文件 \(在 Visual C\# 或 MainPage.xaml.vb 的 MainPage.xaml.cs Visual Basic\) 中，添加以下命名空间引用。  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. 在类的顶部添加下面的变量声明：  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. 用以下代码替换 `UserControl_Loaded` 过程。  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     确保用运行 SharePoint 服务器的名称替换 *ServerName* 占位符。  
  
12. 将下列错误处理过程。  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## 修改 Silverlight Web 部件  
 改变 Silverlight Web 部件项目的属性来启用 Silverlight 调试。  
  
#### 修改 Silverlight web 部件  
  
1.  打开 Silverlight web 部件工程（**SLWebPartTest**）的快捷菜单，然后选择**“属性”**。  
  
2.  在**“属性”**窗口中，选择**SharePoint**选项卡。  
  
3.  如果尚未选中，则选择 **启用 Silverlight 调试 \(而不是脚本调试\)** 复选框。  
  
4.  保存项目。  
  
##  <a name="BKMK_testSLApp"></a> 测试 Silverlight Web 部件  
 测试 SharePoint 的新 Silverlight Web 部件以确保其正确显示 SharePoint 列表数据。  
  
#### 测试 Silverlight Web 部件  
  
1.  选择 F5 键生成并运行 SharePoint 解决方案。  
  
2.  在 SharePoint 中，在 **网站操作** 菜单中，选择 **新建网页**。  
  
3.  在 **新建网页** 对话框中，键入标题，如 SL Web 部件测试，然后选择 **创建** 按钮。  
  
4.  在网页设计器，**编辑工具** 选项卡上，选择 **插入**。  
  
5.  在选项卡条，请选择 **Web 部件**。  
  
6.  在 **类别** 框中，选择 **自定义** 文件夹。  
  
7.  在 Silverlight **Web 部件** 列表中，选择Silverlight Web 部件，然后选择 **添加** 按钮将 Web 部件添加到设计器。  
  
8.  在向所有您想要的网页添加内容之后，选择 **页** 选项卡，然后在工具栏上选择 **保存 & 关闭** 按钮。  
  
     Silverlight Web 部件应当显示 SharePoint 网站的公告数据。  默认情况下，站点中页面在 SharePoint 中列出。  
  
    > [!NOTE]  
    >  当访问在 Silverlight 数据跨域时，Silverlight 防止使用可用于 Web 应用程序的安全漏洞。  当访问在 Silverlight 中的远程数据时，如果您遇到问题，请参见 [利用域服务可用跨边界](http://go.microsoft.com/fwlink/?LinkId=223276)。  
  
## 请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [部署、发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  