---
title: "SharePoint 项目和项目项模板"
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
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 项目与项目项模板"
  - "Visual Studio 中的 SharePoint 开发, 模板"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# SharePoint 项目和项目项模板
  以下各节描述了可用的 SharePoint 项目和项目项模板以及如何使用它们。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> 项目和项目项模板概述  
 在 Visual Studio 中创建新的 SharePoint 项目中时，SharePoint 项目添加到解决方案中与该项目类型所需的项目项的所有。  例如，如果创建 Silverlight Web 部件项目时，Visual Studio 创建一个解决方案包含可视 Web 部件项目项和 Silverlight 应用程序的项目项，以及所需的项目项的所有文件。  项目项模板用于将项目项添加到现有 SharePoint 项目，如添加事件接收器、 网站栏或列表。  
  
 SharePoint 基础知识有关的信息，请参阅 [SharePoint 基础构造块](http://go.microsoft.com/fwlink/?LinkId=179404)。  高级的用户可以创建自定义项目模板和项目项模板。  有关详细信息，请参阅 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> 项目模板  
 下面是 SharePoint 项目模板的列表。  若要查看中的 SharePoint 项目模板在 Visual Studio 中， **新项目** 对话框中，展开  **SharePoint** 下任何一个节点 **Visual C\#** 或 **Visual Basic**，然后选择  **2010年**。  
  
### SharePoint 2010 项目  
 内容的 *SharePoint 2010 项目*都包括在每个 SharePoint 项目模板。  SharePoint 2010 项目包含：  
  
-   一个项目文件。  
  
-   项目属性页。  
  
-   A **引用**文件夹，其中列出了所有在项目中的程序集引用。  
  
-   A **功能**文件夹，其中包含用于将功能部署到 SharePoint 服务器的.feature 配置文件。  
  
-   A **包**包含 Package.package 文件，用于将解决方案部署到 SharePoint 文件夹。  
  
-   使用强名称为程序集签名的一个 key.snk （强名称密钥） 文件增强的安全性。  
  
### SharePoint 2010 Silverlight Web 部件  
 *SharePoint 2010 Silverlight Web 部件*项目，您可以创建显示 Silverlight 应用程序中的 SharePoint web 部件。  在创建此项目时，可以指定要添加到该新的 Silverlight 应用程序还是引用现有。  有关详细信息，请参阅[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)和  [演练：创建显示 SharePoint OData 的 Silverlight Web 部件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### SharePoint 2010 可视 Web 部件  
 A  *SharePoint 2010 可视 Web 部件* 项目包括 Elements.xml 定义文件中，  **Web 部件** 项目，和一个 **用户控件**项。  您可以通过拖动或从 Visual Studio 工具箱中的控件复制到用户控件的图面设计的可视 web 部件的外观。  有关详细信息，请参阅[如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和 [构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### 导入 SharePoint 2010 解决方案包  
 *导入 SharePoint 2010 解决方案包*项目，可以导入全部或部分现有的 SharePoint 2010 网站，到 SharePoint 解决方案 \(.wsp\) 文件，导出到 Visual Studio。  一旦导入到 Visual Studio，可以自定义它的项，并重新部署。  有关详细信息，请参阅 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### 导入可重用的 SharePoint 2010 工作流  
 *导入可重用的 SharePoint 2010 流*项目，可以导入到 Visual Studio 创建 SharePoint 设计 2010 年的可重用的声明性工作流。  从 SharePoint 网站为.wsp 文件导出工作流。  导入到 Visual Studio，可以进行自定义，向其中添加代码，然后将它部署到 SharePoint 网站。  有关详细信息，请参阅 [演练：将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> 项目项模板  
 下面是 SharePoint 项目项模板的列表。  项目项模板将文件添加到 SharePoint 解决方案以支持 SharePoint 站点列、 列表、 内容类型等的功能。  例如，向解决方案中添加一个网站栏添加一个包含的 Elements.xml 定义文件的站点列项目。  添加可视 web 部件将可视 web 部件项目添加到解决方案中包含的 Elements.xml 文件、 用户控件项和一个可视 web 部件项中。  
  
 若要查看中的 SharePoint 项目项模板中， **解决方案资源管理器**、 打开 SharePoint 项目中，快捷菜单，然后选择 **添加**， **新项**。  展开 **SharePoint** 下任何一个节点 **Visual C\#** 或 **Visual Basic**，然后选择  **2010年**。  
  
### 应用程序页 （仅服务器场解决方案）  
 **应用程序页面 （场解决方案仅）** 项，您可以设计 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]SharePoint 站点的网页。  应用程序页可以使用仅在服务器场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅[如何：创建应用程序页](../sharepoint/how-to-create-an-application-page.md)和 [应用程序 \_layouts 网页类型](http://go.microsoft.com/fwlink/?LinkId=179434)。  
  
### 业务数据连接模型 （仅适用于场解决方案）  
 A **业务数据连接模型 （场解决方案仅\)** 项，您可以将业务数据集成到 SharePoint。  业务数据可以来自于后端服务器应用程序，如 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]，注册和服务公布协议 \(SAP\)。  业务数据连接模型只采用场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅 [如何：创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)，   [如何：使用资源文件指定本地化名称、属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，和 [新增： Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411)。  
  
### 内容类型  
 *内容类型*项目，您可以创建基于现有的 （基本） 内容类型，如文档、 公告或任务的自定义内容类型。  自定义的内容类型与基内容类型以及任何您定义的站点列 （字段） 提供相同的特性和字段。  例如，可以创建基于汇集在 SharePoint 中的基本联系内容类型的自定义联系人内容类型。  可以通过更改现有的网站列，或将更多的站点列添加到已包含在基内容类型的自定义内容类型。  
  
> [!NOTE]  
>  由于 SharePoint 的限制，不能创建沙盒解决方案的内容类型所基于的服务器场解决方案内容类型。  
  
 有关详细信息，请参阅[演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和 [构建基块： 内容类型](http://go.microsoft.com/fwlink/?LinkId=179413)。  
  
### 空元素  
 *空元素*最常用于定义缺少某个项目或项目项模板在 Visual Studio 中的 SharePoint 项目项。  当您向项目中添加一个空元素时，一个节点名为 \[x\] EmptyElement（其中 \[x\] 一个唯一的编号） 创建。  EmptyElement \[x\] 包含名为 Elements.xml 的单个文件。  使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]语句 Elements.xml 中定义所需的元素。  
  
### 事件接收器  
 *事件接收器*处理项目在 SharePoint 网站，如某一项添加到列表时，web 项被删除时，或工作流启动时的事件。  事件接收器项目项模板，您可以处理  
  
-   事件列表  
  
-   列表项事件  
  
-   列表电子邮件事件  
  
-   Web 事件  
  
-   列表中的工作流事件  
  
 事件接收器项目项创建**事件接收器** 与单个类文件，其中包含有关的所有事件的事件处理程序中的项目创建时所指定的文件夹  **SharePoint 自定义向导**。   event receiver类可以处理时添加、 更新、 删除或移除项目，如文件、 字段、 项目、 列表、 附件、 web 部件和工作流，在 SharePoint 站点发生的事件。  有关详细信息，请参阅[如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)和 [构建基块： 事件处理](http://go.microsoft.com/fwlink/?LinkId=179416)。  
  
### 列表  
 列表是可重复使用基础 SharePoint 列表定义的实例，如日历或任务列表。  后向解决方案中添加一个列表，列表设计器可以向列表中添加站点列并创建自定义列表的列。  这包括网站内容的类型中的列。  您可以指定*查看*列表，从而确定将出现在列表中的列。  有关详细信息，请参阅[演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和 [构建基块： 列表和文档库](http://go.microsoft.com/fwlink/?LinkId=179421)。  
  
### 模块  
 *模块* （不要混淆与 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]模块） 包含要部署到 SharePoint 服务器，例如，图像或注释的所有文件。  模块项目项包含**模块**节点。  模块节点包含两个项目项模板： XML 定义文件，它将作为模块的清单，以及 sample.txt 文件中，占位符文件。  有关详细信息，请参阅[使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)和 [模块](http://go.microsoft.com/fwlink/?LinkId=179425)。  
  
### 顺序工作流 （仅服务器场解决方案）  
 A *的顺序工作流*是一系列业务逻辑步骤，直到完成最后一个步骤按顺序执行。  顺序工作流用于管理流程涉及到 SharePoint 项 （如列表和文档。  您可以创建站点级 （全局） 工作流或列表级 （本地） 工作流，并可以选择是否自动或手动启动工作流。  此项目项仅用于场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)，   [SharePoint Server 2010 中的工作流](http://go.microsoft.com/fwlink/?LinkId=260555)，和 [新增： 工作流改进](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### Silverlight Web 部件  
 *Silverlight web 部件*项目项，您可以创建显示 Silverlight 应用程序中的 SharePoint web 部件。  此项目项添加到您的解决方案时，您可以选择是否要添加新的 Silverlight 应用程序或以后引用现有。  有关详细信息，请参阅[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)和  [演练：创建显示 SharePoint OData 的 Silverlight Web 部件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### 网站列  
 A *网站列*，也称为 *字段*，是最基本的元素，您可以将其添加到 SharePoint 项目之一。  网站列代表一种类型的数据，如电话号码、 文本注释或在联系人名单中联系人的市\/县名。  有关详细信息，请参阅[创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)和 [列](http://go.microsoft.com/fwlink/?LinkId=226840)。  
  
### 站点定义 （仅服务器场解决方案）  
 *网站定义*项目项包含站点定义文件夹，其中包含以下文件：  
  
-   默认的.aspx 页，用作网站默认的 web 页。  
  
-   定义了站点的组件一个 onet.xml 文件。  
  
-   指定显示在网站定义配置 webtemp xml 文件**模板选择** 部分中的 **新的 SharePoint 网站**页。  
  
 添加站点定义后，您将添加代码和文件来引入功能。  此项目项仅用于场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅[创建 SharePoint 网站定义](../sharepoint/creating-site-definitions-for-sharepoint.md)和 [网站定义和配置](http://go.microsoft.com/fwlink/?LinkId=260554)。  
  
### 状态机工作流 （仅服务器场解决方案）  
 A *状态机工作流*是一组业务逻辑状态、 转换和操作。  状态机工作流中的步骤不会执行的顺序 ； 相反，它们触发由操作和状态。  顺序工作流，如状态机工作流是与 SharePoint 项 （如列表和文档相关联。  同样，可以创建网站级 （全局） 工作流或列表级 （本地） 工作流。  此外，您还可以选择是否自动或手动启动工作流。  此项目项仅用于场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)，   [SharePoint Server 2010 中的工作流](http://go.microsoft.com/fwlink/?LinkId=260555)，和 [新增： 工作流改进](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### 用户控件 （仅服务器场解决方案）  
 A *用户控件*是自定义的、 可重复使用的控件，可以向其中添加其他 ASP.NET 控件和 SharePoint 控件。  可以将用户控件添加到应用程序页和 web 部件在 SharePoint 中运行的。  此项目项仅用于场解决方案。  您可以添加此项目项仅为场解决方案。  有关详细信息，请参阅[为 Web 部件或应用程序页创建可重用控件](http://go.microsoft.com/fwlink/?LinkId=226841)。  
  
### 可视 Web 部件  
 A *可视 web 部件* 项目项包括 Elements.xml 定义文件中，  **Web 部件** 项目，和一个 **用户控件**项。  您可以通过拖动或从 Visual Studio 工具箱中的控件复制到用户控件的图面设计的可视 web 部件的外观。  有关详细信息，请参阅[如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和 [构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### Web 部件  
 A  *web 部件*是在一种特殊类型的网页 （称为 Web 部件页中运行一个服务器端控件。  它们是在 SharePoint 网站显示的页的构建基块。  Web 部件项提供了使您可以设计一个 SharePoint 网站的 web 部件的文件。  有关详细信息，请参阅[如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)和 [构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 产品和技术](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  