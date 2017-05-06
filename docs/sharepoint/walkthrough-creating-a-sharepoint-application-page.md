---
title: "演练：创建 SharePoint 应用程序页"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "应用程序页 [Visual Studio 中的 SharePoint 开发]，开发"
  - "应用程序页 [Visual Studio 中的 SharePoint 开发]，创建"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 演练：创建 SharePoint 应用程序页
  “应用程序页”是 ASP.NET 页的专用形式。  应用程序页包含与 SharePoint 母版页合并的内容。  有关更多信息，请参见[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 本演练演示如何使用本地 SharePoint 站点创建应用程序页并调试该页。  该页显示了每个用户在服务器场中的所有网站中创建并修改的所有项。  
  
 本演练阐释了以下任务：  
  
-   创建 SharePoint 项目。  
  
-   向该 SharePoint 项目添加应用程序页。  
  
-   向该应用程序页添加 ASP.NET 控件。  
  
-   在 ASP.NET 控件后添加代码。  
  
-   测试应用程序页。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   支持的 Windows 和 SharePoint 版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] 或者是 Visual Studio 旗舰版和 Visual Studio 高级专业版中的某个版本。  
  
## 创建 SharePoint 项目  
 首先，创建一个**“空 SharePoint 项目”**。  然后，向该项目添加**“应用程序页”**项。  
  
#### 创建 SharePoint 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  打开“新建项目”对话框，展开要使用的语言下的“Office\/SharePoint”节点，然后选择“SharePoint 解决方案”节点。  
  
3.  在“Visual Studio 已安装模板”窗格中，选择“SharePoint 2010 \- 空项目”模板。  将项目命名为“MySharePointProject”，并选中“确定”按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  使用此向导可以选择用于调试项目的站点以及解决方案的信任级别。  
  
4.  选择“部署为场解决方案”选项按钮，然后选择“完成”按钮以接受默认的本地 SharePoint 站点。  
  
## 创建应用程序页  
 若要创建应用程序页，请向该项目添加**“应用程序页”**项。  
  
#### 创建应用程序页  
  
1.  在“解决方案资源管理器”中，选择“MySharePointProject”项目。  
  
2.  在菜单栏上，依次选择“项目”、“添加新项”。  
  
3.  在“添加新项”对话框中，选择“应用程序页（仅场解决方案）”模板。  
  
4.  将页命名为“SearchItems”，然后选择“添加”按钮。  
  
     Visual Web Developer 设计器将在“源”视图中显示应用程序页，您可以在该视图中查看此页的 HTML 元素。  该设计器显示多个 <xref:System.Web.UI.WebControls.Content> 控件的标记。  每个控件均映射到在默认应用程序母版页中定义的 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 控件。  
  
## 设计应用程序页的布局  
 通过“应用程序页”项，您可以使用设计器将 ASP.NET 控件添加到应用程序页中。  此设计器即是在 Visual Web Developer 中使用的设计器。  按照任何标准 ASP.NET 页的设计方式，将标签、单选按钮列表和表添加到设计器的“源”视图中，并设置相应属性。  
  
 有关使用 Visual Web Developer 中的设计器的更多信息，请参见[Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
#### 设计应用程序页的布局  
  
1.  在菜单栏上，依次选择“查看”、“工具箱”。  
  
2.  在“工具箱”的“标准”节点中，执行以下步骤之一：  
  
    -   打开“标签”项的快捷菜单，选择“复制”，然后打开设计器中“PlaceHolderMain”内容控件下行的快捷菜单，然后选择“粘贴”。  
  
    -   将“标签”项从“工具箱”拖动到“PlaceHolderMain”内容控件的主体上。  
  
3.  重复上面的步骤，将“下拉列表”项和“表”项添加至“PlaceHolderMain”内容控件。  
  
4.  在设计器中，将标签控件的 `Text` 特性的值更改为“显示所有项”。  
  
5.  在设计器中，用以下 XML 替换 `<asp:DropDownList>` 元素。  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## 处理该页上的控件的事件  
 按照任何 ASP.NET 页的控件的处理方式，处理应用程序页中的控件。  在此过程中，您将处理下拉列表的 `SelectedIndexChanged` 事件。  
  
#### 处理该页上的控件的事件  
  
1.  在“视图”菜单上，选择“代码”。  
  
     应用程序页代码文件随即在代码编辑器中打开。  
  
2.  将以下方法添加到 `SearchItems` 类中。  此代码通过调用将在本演练的稍后部分中创建的方法，来处理 <xref:System.Web.UI.WebControls.DropDownList> 的 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> 事件。  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  将以下语句添加到应用程序页代码文件的顶部。  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  将以下方法添加到 `SearchItems` 类中。  此方法循环访问服务器场中的所有网站，并搜索由当前用户创建或修改的项。  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  将以下方法添加到 `SearchItems` 类中。  此方法显示表中由当前用户创建或修改的项。  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## 测试应用程序页  
 在运行项目时，SharePoint 网站将打开，并显示应用程序页。  
  
#### 测试应用程序页  
  
1.  在“解决方案资源管理器”中，打开应用程序页的快捷菜单，然后选择“设置为启动项”。  
  
2.  选择 F5 键。  
  
     SharePoint 网站将打开。  
  
3.  在应用程序页上，选择“由我修改”选项。  
  
     此时将刷新该应用程序页，并显示您在服务器场中的所有站点中修改的所有项。  
  
4.  在应用程序页中，在列表中选择“由我创建”。  
  
     此时将刷新该应用程序页，并显示您在服务器场中的所有网站中创建的所有项。  
  
## 后续步骤  
 有关 SharePoint 应用程序页的更多信息，请参见[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 通过使用以下主题中介绍的 Visual Web Designer，可以了解有关如何设计 SharePoint 页内容的更多内容：  
  
-   [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 请参阅  
 [如何：创建应用程序页](../sharepoint/how-to-create-an-application-page.md)   
 [Application \_layouts Page Type](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  