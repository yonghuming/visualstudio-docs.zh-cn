---
title: "演练：导入带有图像的自定义母版页和网站页 | Microsoft Docs"
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
helpviewer_keywords: 
  - "导入项 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 导入项"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 演练：导入带有图像的自定义母版页和网站页
  本演练演示如何将 SharePoint 自定义母版页和包含图像的网站页面导入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中。  
  
 本演练演示如何完成以下任务：  
  
-   在 SharePoint Designer 中使用图像创建自定义母版页和网站页面。  
  
-   将自定义母版页、图像和网站页面导出为 SharePoint 解决方案 \(.wsp\) 文件。  
  
-   使用“导入 SharePoint 解决方案包”项目将 .wsp 文件导入和部署到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 若要完成本演练，您必须具有以下组件：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio。  
  
-   SharePoint Designer 2010。  
  
## 在 SharePoint Designer 中创建项  
 此示例演示如何在 SharePoint Designer 中创建要导出的三个项：一个自定义母版页、一个引用自定义母版页的网站页面和一个要在网站页面上显示的图像文件。  该图像会添加到 SharePoint 中的 \/images\/ 文件夹。  
  
#### 在 SharePoint Designer 中创建一个自定义母版页  
  
1.  在 SharePoint Designer 中的导航窗格中，选择**“母版页”**站点对象。  
  
2.  在 **母版页** 功能区上，选择 **空白母版页**。  
  
3.  选择新母版页，然后，在 **母版页** 功能区上，选择 **编辑文件**。  
  
4.  在 SharePoint Designer 的底部，选择**“代码”**选项卡。  
  
5.  将现有标记替换为以下标记。  
  
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
  
6.  保存页，选择 **母版页** 选项卡，并将母版页进行重命名为 **mybasic1.master**。  
  
## 将图像添加到 SharePoint Designer 中的内容数据库  
 此时可添加一个图像以在网站页面上显示。  该图像将部署到 SharePoint 内容数据库。  
  
#### 将一个图像添加到 SharePoint Designer 中的内容数据库  
  
1.  在导航窗格，选择 **所有文件** 的站点对象，然后，在树视图中，选择 **图像** 文件夹。  
  
2.  在 **所有文件** 功能区中，选择 **导入文件**，选择所选文件，然后选择 **确定** 按钮。  在此示例中，该文件名为 **myimg1.png**。  
  
     （可选）您可以创建子文件夹以帮助组织图像。  
  
3.  关闭**“导入”**对话框。  
  
## 创建网站页面  
 此基本网站页面使用自定义母版页，并显示您在上一步中添加的图像。  
  
#### 创建网站页面  
  
1.  在导航窗格中，选择 **站点页面** 对象。  
  
2.  在 **页** 功能区上，选择 **页** 按钮，选择 **ASPX** 页类型，然后将新文件命名为 **mycontentpage1.aspx**。  
  
     （可选）您可以创建子文件夹以帮助组织网站页面。  
  
3.  在站点页列表中，选择**“MyContentPage1.aspx”**打开其属性页，然后选择该页底部的**“编辑文件”**链接。  
  
     如果消息显示并指出，此页不能包含任何可在安全模式下编辑的区域，并且询问是否在先行模式打开时，请选择 **是** 按钮。  
  
4.  在该页底部，选择**“代码”**按钮。  
  
5.  将现有标记替换为以下标记。  
  
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
  
## 从 SharePoint 导出项  
 将 SharePoint 中的项导出为 SharePoint 解决方案 \(.wsp\) 文件。  
  
#### 从 SharePoint Designer 中导出项  
  
1.  在 SharePoint 设计器，导航窗格中，选择 **工作组网站** 对象，然后，在 **网站** 功能区上，选择 **另存为模板**。  
  
2.  在**“另存为模板”**对话框中，键入文件名和模板名，选中**“包含内容”**复选框，然后选择**“确定”**按钮。  
  
     这会将网站内容保存到 .wsp 文件中。  
  
3.  在导出解决方案后，选择**“解决方案库”**链接以显示可用解决方案文件的列表。  
  
4.  打开新 .wsp 文件的快捷菜单，然后选择 **将目标另存为** 将其保存到系统。  
  
## 将项导入 Visual Studio 中  
 导入 .wsp 文件到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  导入内容后，您可以对它进行自定义，添加更多项，然后部署它。  
  
#### 将 .wsp 文件中的项导入 Visual Studio 中  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，创建一个**“导入 SharePoint 2010 解决方案包”**项目。  
  
2.  在**“选择要导入的项”**页上**“模块”**下的**“类型”**列中，仅选择下表中的复选框文件以进行导入。  
  
    |文件名|说明|  
    |---------|--------|  
    |\_catalogsmasterpage\_|自定义母版页。|  
    |images\_|SharePoint 文件系统中的图像文件。|  
    |SitePages\_|网站页面。|  
  
3.  选择 **完成** 按钮导入所选项。  
  
4.  在**“解决方案资源管理器”**中，选择 \_catalogsmasterpage\_ 节点，然后将**“部署冲突解决方法”**属性的值设置为**“自动”**。  
  
     这有助于确保自动解决任何部署冲突。  
  
5.  如果新母版页的名称与现有页的名称相同，请确保现有页在 SharePoint Designer 中未标记为默认母版页或自定义母版页。  
  
     如果现有母版页标记为默认母版页或自定义母版页，则您会收到一条部署错误，表明无法删除母版页。  若要避免此问题，请执行下列操作：  
  
    -   如果现有母版页设置为默认母版页，则暂时将其他母版页设置为默认母版页。  在将这些文件部署到 SharePoint 后，请将新母版页设置为默认母版页。  
  
    -   如果现有母版页设置为自定义母版页，则暂时将其他母版页设置为自定义母版页。  在将这些文件部署到 SharePoint 后，请将新母版页设置为自定义母版页。  
  
6.  在菜单栏上，依次选择**“生成”**、**“部署解决方案”**。  
  
7.  打开 SharePoint 网站以查看部署项。  
  
 也可以通过另一种方式将这些文件导入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，并将它们部署到 SharePoint，即将这些文件添加到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的模块中。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][如何：导入母版页或主题](../sharepoint/how-to-import-a-master-page-or-theme.md)和[使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## 请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  