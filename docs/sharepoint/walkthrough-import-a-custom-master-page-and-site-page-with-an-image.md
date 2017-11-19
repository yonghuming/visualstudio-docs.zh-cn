---
title: "演练： 导入自定义母版页和网站页的映像 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5126e15daa8cbc22f4b64be0bb2bb2f3e0bb6b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>演练：导入带有图像的自定义母版页和网站页
  本演练演示如何导入 SharePoint 的自定义母版页和网站页具有图像成为[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。  
  
 本演练演示如何完成以下任务：  
  
-   在 SharePoint Designer 中使用的映像创建自定义母版页和网站页。  
  
-   将自定义母版页、 映像和网站页导出到的 SharePoint 解决方案 (.wsp) 文件。  
  
-   导入和部署将.wsp 文件[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用导入 SharePoint 解决方案包项目的 SharePoint 项目。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你必须具有以下组件来完成本演练：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][开发 SharePoint 解决方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   SharePoint Designer 2010。  
  
## <a name="create-items-in-sharepoint-designer"></a>在 SharePoint Designer 中创建项目  
 此示例演示如何在 SharePoint Designer 中创建三个项，用于导出： 自定义母版页、 网站页引用自定义母版页和要在网站页面上显示的图像文件。 将图像添加到 SharePoint 中的 /images/ 文件夹中。  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>若要在 SharePoint Designer 中创建自定义母版页  
  
1.  在 SharePoint 设计器中，在导航窗格中，选择**母版页**站点对象。  
  
2.  上**母版页**功能区上，选择**空白母版页**。  
  
3.  选择新的主页上，然后在**母版页**功能区上，选择**编辑文件**。  
  
4.  在 SharePoint 设计器的底部，选择**代码**选项卡。  
  
5.  将现有的标记替换为以下标记。  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  保存页中，选择**母版页**选项卡，然后重命名为母版页**mybasic1.master**。  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>将映像添加到 SharePoint 设计器中的内容数据库  
 现在你可以添加要在网站页面上显示的图像。 映像部署到 SharePoint 内容数据库。  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>若要将图像添加到 SharePoint Designer 中的内容数据库  
  
1.  在导航窗格中，选择**所有文件**站点对象，，然后，在树视图中，选择**映像**文件夹。  
  
2.  上**所有文件**功能区上，选择**导入文件**，选择你选择的文件，然后选择**确定**按钮。 在此示例中，该文件被命名为**myimg1.png**。  
  
     （可选） 你可以创建一个子文件夹，以帮助组织映像。  
  
3.  关闭**导入**对话框。  
  
## <a name="create-a-site-page"></a>创建网站页  
 本页基本站点使用自定义母版页，并显示你在上一步中添加的映像。  
  
#### <a name="to-create-a-site-page"></a>若要创建站点页  
  
1.  在导航窗格中，选择**网站页**对象。  
  
2.  上**页**功能区上，选择**页**按钮，选择**ASPX**页上，键入，并将其命名新文件**mycontentpage1.aspx**。  
  
     （可选） 你可以创建一个子文件夹，以帮助组织网站页。  
  
3.  在站点页列表中，选择**MyContentPage1.aspx**以打开其属性页中，然后，在页面底部，选择**编辑文件**链接。  
  
     如果显示消息和显示此页不包含在安全模式下编辑任何区域，会询问你是否要在高级模式中打开此页中，选择**是**按钮。  
  
4.  在页面底部，选择**代码**按钮。  
  
5.  将现有的标记替换为以下标记。  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  保存更新的网站页面。  
  
## <a name="export-the-items-from-sharepoint"></a>导出从 SharePoint 项  
 将项目从 SharePoint 导出到的 SharePoint 解决方案 (.wsp) 文件。  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>若要从 SharePoint 设计器中导出项目  
  
1.  在 SharePoint 设计器中，在导航窗格中，选择**团队站点**对象，然后在**站点**功能区上，选择**另存为模板**。  
  
2.  在**另存为模板**对话框框中，输入文件名称和模板名称，选择**内容包括**复选框，然后依次**确定**按钮。  
  
     此操作会将该站点的内容保存在.wsp 文件中。  
  
3.  解决方案导出后，请选择**解决方案库**链接以显示可用的解决方案文件的列表。  
  
4.  打开新的.wsp 文件中的快捷菜单，然后选择**目标另存为**将它保存到系统。  
  
## <a name="import-the-items-into-visual-studio"></a>导入 Visual Studio 项  
 .Wsp 文件导入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 将内容导入后，可以自定义它、 添加更多项，以及然后将其部署。  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>若要将项从.wsp 文件导入 Visual Studio  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，创建**导入 SharePoint 2010 解决方案包**项目。  
  
2.  上**选择要导入的项**页上，在**模块**中**类型**列中，导入为下表中选择仅将文件对应的复选框。  
  
    |文件名|描述|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|自定义母版页。|  
    |images_|SharePoint 文件系统中的图像文件。|  
    |SitePages_|网站页中。|  
  
3.  选择**完成**按钮导入所选的项目。  
  
4.  在**解决方案资源管理器**，选择 _catalogsmasterpage\_节点，并将的值设置其**部署冲突解决方法**属性**自动**。  
  
     这有助于确保自动解决任何部署冲突。  
  
5.  如果你的新主页面具有同名的现有的页面，请确保现有页未标记为默认母版页或在 SharePoint Designer 中自定义母版页。  
  
     如果现有的主页面标记为默认母版页或自定义母版页中，你将获取部署错误，指出主控页，不能删除。 若要避免此问题，请执行此操作：  
  
    -   如果现有的主控页设置为默认母版页，暂时将另一个母版页设置为默认母版页。 将文件部署到 SharePoint 后，请为默认母版页设置你的新主页面。  
  
    -   如果现有的主控页设置为自定义母版页，暂时将另一个母版页设置为自定义母版页。 将文件部署到 SharePoint 后，请为自定义母版页设置你的新主页面。  
  
6.  在菜单栏上，选择**生成**，**部署解决方案**。  
  
7.  打开 SharePoint 站点，以查看已部署的项。  
  
 文件导入到一种备用方法[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和将其部署到 SharePoint 是将文件添加到中的模块[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][如何： 导入母版页或主题](../sharepoint/how-to-import-a-master-page-or-theme.md)和[使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## <a name="see-also"></a>另请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  