---
title: "演练： 创建 SharePoint 应用程序页 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e49e8d50905dc0bb0b3c104a7133fe7435e2e944
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>演练：创建 SharePoint 应用程序页
  应用程序页是一种特殊的形式的 ASP.NET 页。 应用程序页包含与 SharePoint 母版页合并的内容。 有关详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 本演练演示了如何创建的应用程序页，然后调试它使用本地 SharePoint 站点。 此页显示每个用户具有创建或修改在上的服务器场的所有站点中的所有项。  
  
 本演练阐释了以下任务：  
  
-   创建 SharePoint 项目。  
  
-   向 SharePoint 项目中添加的应用程序页。  
  
-   将 ASP.NET 控件添加到应用程序页。  
  
-   在 ASP.NET 控件的后面添加代码。  
  
-   测试应用程序页。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   受支持的 Windows 和 SharePoint 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]或某一版本的 Visual Studio Ultimate 或 Visual Studio 高级专业版。  
  
## <a name="creating-a-sharepoint-project"></a>创建 SharePoint 项目  
 首先，创建**空 SharePoint 项目**。 稍后，你将添加**应用程序页**到此项目的项。  
  
#### <a name="to-create-a-sharepoint-project"></a>若要创建一个 SharePoint 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  打开**新项目**对话框框中，展开**Office/SharePoint**你想要使用，然后选择的语言下节点**SharePoint 解决方案**节点。  
  
3.  在**Visual Studio 已安装的模板**窗格中，选择**SharePoint 2010-空项目**模板。 将项目**MySharePointProject**，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。 此向导，可选择将用于调试项目和解决方案的信任级别的站点。  
  
4.  选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮以接受默认的本地 SharePoint 站点。  
  
## <a name="creating-an-application-page"></a>创建应用程序页  
 若要创建的应用程序页，添加**应用程序页**到项目的项。  
  
#### <a name="to-create-an-application-page"></a>若要创建的应用程序页  
  
1.  在**解决方案资源管理器**，选择**MySharePointProject**项目。  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  在**添加新项**对话框框中，选择**应用程序页上 (仅场解决方案**模板。  
  
4.  将该页命名为**SearchItems**，然后选择**添加**按钮。  
  
     Visual Web Developer 设计器显示在应用程序页上**源**视图可以看到此页的 HTML 元素的位置。 设计器显示若干个标记<xref:System.Web.UI.WebControls.Content>控件。 每个控件映射到<xref:System.Web.UI.WebControls.ContentPlaceHolder>默认应用程序母版页中定义的控件。  
  
## <a name="designing-the-layout-of-the-application-page"></a>设计应用程序页的布局  
 应用程序页上项，您可以使用设计器将 ASP.NET 控件添加到应用程序页。 此设计器是在 Visual Web Developer 中使用的同一设计器。 添加标签、 单选按钮列表中和表的**源**的设计器中，查看，然后设置属性，就像设计任何标准的 ASP.NET 页时。  
  
#### <a name="to-design-the-layout-of-the-application-page"></a>若要设计应用程序页的布局  
  
1.  在菜单栏上，依次选择“视图”、“工具箱”。  
  
2.  中的标准节点**工具箱**，执行以下步骤之一：  
  
    -   打开的快捷菜单**标签**项，选择**复制**，打开的行的快捷菜单**PlaceHolderMain**内容控件在设计器中，然后选择**粘贴**。  
  
    -   拖动**标签**项从**工具箱**到正文**PlaceHolderMain**内容控件。  
  
3.  重复上述步骤以添加**DropDownList**项和**表**项以**PlaceHolderMain**内容控件。  
  
4.  在设计器中，将更改的值`Text`该标签控件的属性**显示所有项**。  
  
5.  在设计器中，将`<asp:DropDownList>`使用以下 XML 元素。  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## <a name="handling-the-events-of-controls-on-the-page"></a>处理的页上的控件的事件  
 处理应用程序页中的控件，就像任何 ASP.NET 页。 在此过程中，将处理`SelectedIndexChanged`的下拉列表的事件。  
  
#### <a name="to-handle-the-events-of-controls-on-the-page"></a>若要处理的页上的控件事件  
  
1.  上**视图**菜单上，选择**代码**。  
  
     应用程序页代码文件在代码编辑器中打开。  
  
2.  将以下方法添加到 `SearchItems` 类。 此代码处理<xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>事件<xref:System.Web.UI.WebControls.DropDownList>通过调用将创建在本演练后面的方法。  
  
     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]  
  
3.  将以下语句添加到应用程序页面代码文件的顶部。  
  
     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]  
  
4.  将以下方法添加到 `SearchItems` 类。 此方法循环访问所有站点上的服务器场，并搜索由当前用户创建或修改的项。  
  
     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]  
  
5.  将以下方法添加到 `SearchItems` 类。 此方法会显示通过表中的当前用户创建或修改的项。  
  
     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]  
  
## <a name="testing-the-application-page"></a>测试应用程序页  
 运行项目时，会打开 SharePoint 站点，将显示的应用程序页。  
  
#### <a name="to-test-the-application-page"></a>若要测试应用程序页  
  
1.  在**解决方案资源管理器**，打开应用程序页的快捷菜单，然后选择**设为启动项目**。  
  
2.  选择 F5 键。  
  
     打开 SharePoint 站点。  
  
3.  在应用程序页上，选择**修改由我**选项。  
  
     刷新应用程序页，并显示已在服务器场中的所有站点中修改的所有项。  
  
4.  在应用程序页上，选择**由我创建**列表中。  
  
     刷新应用程序页，并显示已在服务器场中的所有站点中创建的所有项。  
  
## <a name="next-steps"></a>后续步骤  
 有关 SharePoint 应用程序页的详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 你可以了解有关如何通过使用从下面这些主题可视 Web 设计器设计 SharePoint 页内容的详细信息：  
  
-   [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
-   [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建的应用程序页](../sharepoint/how-to-create-an-application-page.md)   
 [应用程序 _layouts 页上，键入](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  