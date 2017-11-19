---
title: "SharePoint 项目和项目项模板 |Microsoft 文档"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 513b2216a99f37ba3aff1174965470b20921072f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint 项目和项目项模板
  下列各节描述了可用的 SharePoint 项目和项目项模板以及如何使用它们。 
  
##  <a name="project-and-project-item-templates-overview"></a>项目和项目项模板概述  
 当在 Visual Studio 中创建新的 SharePoint 项目时，SharePoint 项目添加到与该项目类型所需的项目项的所有解决方案。 例如，如果你创建的 Silverlight Web 部件项目，Visual Studio 将创建包含可视 Web 部件项目项和 Silverlight 应用程序的项目项，以及所需的这些项目项的所有文件的解决方案。 项目项模板用于将项目项添加到现有 SharePoint 项目，例如添加事件接收器、 站点列或列表。  
  
 有关 SharePoint 基础知识的信息，请参阅[SharePoint Foundation 构建基块](http://go.microsoft.com/fwlink/?LinkId=179404)。 高级的用户可以创建自定义项目和项目项模板。 有关详细信息，请参阅[扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)。  
  
##  <a name="project-templates"></a>项目模板  
 下面是 SharePoint 项目模板列表的信息。 若要查看 Visual Studio 中的 SharePoint 项目模板在**新项目**对话框框中，展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**。  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 项目  
 内容*SharePoint 2010 项目*都包括在每个 SharePoint 项目模板。 SharePoint 2010 项目包含：  
  
-   项目文件。  
  
-   在项目属性页。  
  
-   A**引用**其中列出了所有项目中的程序集引用的文件夹。  
  
-   A**功能**包含用来将功能部署到 SharePoint 服务器的.feature 配置文件的文件夹。  
  
-   A**包**包含 Package.package 文件，用于将解决方案部署到 SharePoint 文件夹。  
  
-   用于为对具有强名称程序集进行签名的命名为 key.snk （强名称密钥） 文件增强的安全性。  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight Web 部件  
 *SharePoint 2010 Silverlight Web 部件*项目，可以创建显示 Silverlight 应用程序的 SharePoint web 部件。 在创建此项目时，你可以指定是否添加到该新的 Silverlight 应用程序或引用一个现有。 有关详细信息，请参阅[for SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)和[演练： 为 SharePoint 创建 Silverlight Web 部件该显示 OData](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 可视 Web 部件  
 A *SharePoint 2010 可视 Web 部件*项目包括 Elements.xml 定义文件中， **Web 部件**项，和一个**用户控件**项。 你可以通过拖动或将控件从 Visual Studio 工具箱复制到用户控件的图面中设计的可视 web 部件的外观。 有关详细信息，请参阅[如何： 使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和[构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="import-sharepoint-2010-solution-package"></a>导入 SharePoint 2010 解决方案包  
 *导入 SharePoint 2010 解决方案包*项目让你导入现有的 SharePoint 2010 站点，为 SharePoint 解决方案 (.wsp) 文件，导出到 Visual Studio 的全部或部分。 一旦导入到 Visual Studio 中，可以自定义其项并将它们重新部署。 有关详细信息，请参阅[从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>导入可重用的 SharePoint 2010 工作流  
 *导入可重用 SharePoint 2010 工作流*项目让你导入到 Visual Studio 中在 SharePoint Designer 2010 中创建的可重用的声明性工作流。 工作流导出从 SharePoint 站点为.wsp 文件。 一旦导入到 Visual Studio 中，可以自定义它、 将代码添加到它，以及然后将其部署到 SharePoint 站点。 有关详细信息，请参阅[演练： 将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)。  
  
##  <a name="project-item-templates"></a>项目项模板  
 以下是 SharePoint 项目项模板的列表。 项目项模板将文件添加到 SharePoint 解决方案以支持 SharePoint 功能，如网站栏、 列表和内容类型。 例如，将站点列添加到你的解决方案添加站点列包含的项目，Elements.xml 定义文件。 添加可视 web 部件将可视 web 部件项目添加到包含 Elements.xml 文件、 用户控件项和可视 web 部件项目的解决方案。  
  
 若要查看在 SharePoint 项目项模板，**解决方案资源管理器**，打开 SharePoint 项目的快捷菜单，然后选择**添加**，**新项**。 展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**。  
  
### <a name="application-page-farm-solution-only"></a>应用程序页上 （仅场解决方案）  
 **（仅场解决方案） 应用程序页**项使你能够设计[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]网页上的 SharePoint 站点。 可以仅在场解决方案中使用应用程序页。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[如何： 创建应用程序页](../sharepoint/how-to-create-an-application-page.md)和[应用程序 _layouts 页类型](http://go.microsoft.com/fwlink/?LinkId=179434)。  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>业务数据连接模型 （仅场解决方案）  
 A**业务数据连接模型 （仅场解决方案）**项使你能够将业务数据集成到 SharePoint。 业务数据可以来自从后端服务器应用程序，如[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]，Siebel 和服务广告协议 (SAP)。 业务数据连接模型仅用于场解决方案。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[如何： 创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)，[如何： 使用资源文件指定本地化名称、 属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，和[新增功能： 业务连接服务](http://go.microsoft.com/fwlink/?LinkId=179411)。  
  
### <a name="content-type"></a>内容类型  
 *内容类型*项可让你创建基于现有的 （基） 内容类型，如文档、 公告或任务的自定义内容类型。 自定义的内容类型为基的内容类型与任何你定义的网站栏 （字段） 一起提供的相同的属性和字段。 例如，你可以创建基于传入 SharePoint 基联系人内容类型的自定义联系人内容类型。 你可以通过更改现有的网站栏或将多个站点列添加到已包含在基的内容类型的自定义内容的类型。  
  
> [!NOTE]  
>  由于 SharePoint 限制，无法创建基于沙盒解决方案内容类型的场解决方案内容类型。  
  
 有关详细信息，请参阅[演练： 创建网站栏、 内容类型和 SharePoint 列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和[构建基块： 内容类型](http://go.microsoft.com/fwlink/?LinkId=179413)。  
  
### <a name="empty-element"></a>空元素  
 *空元素*通常用于定义缺少的项目或项目项模板在 Visual Studio 中的 SharePoint 项目项。 当将空元素添加到你的项目时，则节点名为 EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] 包含名为 Elements.xml 单个文件。 使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]语句在 Elements.xml 中定义所需的元素。  
  
### <a name="event-receiver"></a>事件接收器  
 *事件接收器*处理中的 SharePoint 站点，如时将项添加到列表、 web 项目中删除时，或当工作流启动的项的事件。 事件接收器项目项模板让你处理  
  
-   列出的事件  
  
-   列表项事件  
  
-   列出的电子邮件事件  
  
-   Web 事件  
  
-   列表工作流事件  
  
 事件接收器项目项创建**事件接收器**文件夹包含事件处理程序的所有事件创建的项目中时指定的单个类文件与**SharePoint 自定义项向导**。 事件接收器类可以处理添加、 更新、 删除，或移除项，如文件、 字段、 项、 列出、 附件、 web 部件和工作流时，在 SharePoint 站点发生的事件。 有关详细信息，请参阅[如何： 创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)和[构建基块： 的事件处理](http://go.microsoft.com/fwlink/?LinkId=179416)。  
  
### <a name="list"></a>列表  
 列表是可重用基本 SharePoint 列表定义，如日历或任务列表的实例。 添加到你的解决方案的列表后, 列表设计器，可将网站栏添加到列表并创建自定义列表列。 这包括从内容类型的网站栏。 你可以指定*视图*有关列表，用于确定将出现在列表中的列。 有关详细信息，请参阅[演练： 创建网站栏、 内容类型和 SharePoint 列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和[构建基块： 列表和文档库](http://go.microsoft.com/fwlink/?LinkId=179421)。  
  
### <a name="module"></a>模块  
 *模块*(无法将其与混淆[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]模块) 包含你想要部署到 SharePoint 服务器，如图像或说明的任何文件。 模块项目项包含**模块**节点。 模块节点包含两个项目项模板： 充当模块清单，XML 定义文件和 sample.txt 文件，一个占位符文件。 有关详细信息，请参阅[使用模块添加到解决方案中包含文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)和[模块](http://go.microsoft.com/fwlink/?LinkId=179425)。  
  
### <a name="sequential-workflow-farm-solution-only"></a>顺序工作流 （仅场解决方案）  
 A*顺序工作流*是业务逻辑步骤，直到完成的最后一步，在序列中，执行一系列。 顺序工作流用于管理包含 SharePoint 项列表和文档等流程。 你可以创建站点级别 （全局） 工作流或列表级别 （本地） 工作流，并且你可以选择是否工作流以自动或手动。 可以仅在场解决方案中使用此项目项。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流](http://go.microsoft.com/fwlink/?LinkId=260555)，和[新增功能： 工作流改进](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="silverlight-web-part"></a>Silverlight Web 部件  
 *Silverlight web 部件*项目项，可以创建显示 Silverlight 应用程序的 SharePoint web 部件。 当将此项目项添加到你的解决方案时，你可以选择是否添加新的 Silverlight 应用程序或更高版本引用一个现有。 有关详细信息，请参阅[for SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)和[演练： 为 SharePoint 创建 Silverlight Web 部件该显示 OData](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)。  
  
### <a name="site-column"></a>网站栏  
 A*网站栏*，也称为*字段*，是你可以添加到 SharePoint 项目的最基本元素之一。 网站栏表示数据的类型，例如电话号码、 文本注释或联系人列表中的联系人的城市名称。 有关详细信息，请参阅[创建网站栏、 内容类型和列表以供 SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)和[列](http://go.microsoft.com/fwlink/?LinkId=226840)。  
  
### <a name="site-definition-farm-solution-only"></a>站点定义 （仅场解决方案）  
 *站点定义*项目项包含的站点定义文件夹，其中包含以下文件：  
  
-   默认的.aspx 页，为该站点用作默认网页。  
  
-   是定义的站点组件的 onet.xml 文件。  
  
-   指定出现在站点定义配置的 webtemp xml 文件**模板选择**部分**新建 SharePoint 网站**页。  
  
 你添加的站点定义后，你将添加代码和文件引入功能。 可以仅在场解决方案中使用此项目项。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[创建 SharePoint 站点定义](../sharepoint/creating-site-definitions-for-sharepoint.md)和[站点定义和配置](http://go.microsoft.com/fwlink/?LinkId=260554)。  
  
### <a name="state-machine-workflow-farm-solution-only"></a>状态机工作流 （仅场解决方案）  
 A*状态机工作流*是一套业务逻辑状态、 转换和操作。 按顺序; 不执行状态机工作流中的步骤相反，它们由操作和状态触发。 顺序工作流，如状态机工作流将与列表和文档等 SharePoint 项关联。 同样，你可以创建站点级别 （全局） 工作流或列表级别 （本地） 工作流。 你还可以选择是否工作流以自动或手动。 可以仅在场解决方案中使用此项目项。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)， [SharePoint Server 2010 中的工作流](http://go.microsoft.com/fwlink/?LinkId=260555)，和[新增功能： 工作流改进](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### <a name="user-control-farm-solution-only"></a>用户控件 （仅场解决方案）  
 A*用户控件*是可以添加其他 ASP.NET 控件和 SharePoint 控件的自定义、 可重用控件。 用户控件可以添加到应用程序页和 web 部件在 SharePoint 中运行。 可以仅在场解决方案中使用此项目项。 你可以仅向场解决方案中添加此项目项。 有关详细信息，请参阅[为 Web 部件或应用程序页创建可重用控件](http://go.microsoft.com/fwlink/?LinkId=226841)。  
  
### <a name="visual-web-part"></a>可视 Web 部件  
 A*可视 web 部件*项目项包含 Elements.xml 定义文件， **Web 部件**项，和一个**用户控件**项。 你可以通过拖动或将控件从 Visual Studio 工具箱复制到用户控件的图面中设计的可视 web 部件的外观。 有关详细信息，请参阅[如何： 使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和[构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### <a name="web-part"></a>Web 部件  
 A *web 部件*是一个可在一种特殊类型的调用 Web 部件页的页内运行的服务器端控件。 它们是在 SharePoint 站点显示的页的构建基块。 Web 部件项目提供了使你可以设计为 SharePoint 站点的 web 部件的文件。 有关详细信息，请参阅[如何： 创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)和[构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 产品和技术](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
