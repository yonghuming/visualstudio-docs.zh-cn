---
title: "开发 SharePoint 解决方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.ProjectProperties"
  - "VS.SharePointTools.Project.ProjectItemProperties"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发概述"
ms.assetid: 059bce0f-c301-4234-a0b4-9c14b7cdfa3e
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 开发 SharePoint 解决方案
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中可提供多种 SharePoint 项目类型模板，用于创建 SharePoint 站点和站点元素。 有关可用的项目类型的列表，请参阅 [SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。 以下是对 SharePoint 项目元素和属性的说明。

 有关 SharePoint 2013 和 SharePoint 信息添加\-加载项，请参阅 [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) 和 [构建 SharePoint 添加\-单元](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx)。

## <a name="elements-of-a-sharepoint-project"></a>SharePoint 项目元素
 SharePoint 项目中的节点被称为 *SharePoint 项*。 SharePoint 项也可能包含一个或多个称为 *SharePoint 项文件*的子文件，例如， [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 配置文件和 .aspx 窗体等等。

 可以使用“空项目”  模板创建空 SharePoint 项目，然后手动添加项目项，而不是使用已填充项目项文件的项目模板创建项目。 SharePoint 项目可以选择性地包含一个或多个功能文件 \(SharePoint 中激活\) 和在其中分发项目的包文件。

### <a name="special-nodes"></a>特殊节点
 每个 SharePoint 项目都包含两个无法从项目中重命名、删除、剪切、复制，或拖放的节点。 这些节点如下所示：

-   功能

-   package

 即使没有定义项目的功能或包，这两个节点始终都显示在所有 SharePoint 项目中。

#### <a name="features-node"></a>功能节点
 “功能”  节点包含一个或多个 SharePoint 项目功能。 功能是 SharePoint 扩展的容器。 将功能部署到 SharePoint 服务器后，它可以包括在站点定义中或由 SharePoint 站点上的 SharePoint 管理员来单独激活。 有关详细信息，请参阅 [使用功能](http://go.microsoft.com/fwlink/?LinkID=147704)。

 当将某个项（如，内容类型或列表实例）添加到 SharePoint 项目时，那么该项会添加到“功能”  节点的一个功能中。 项的范围决定了将其添加到新功能还是现有功能。 如果新项与现有功能具有相同的范围，那么将此项添加到该功能中。 否则，将该项添加到新功能中。

 若要手动添加一项功能，请执行功能节点的快捷菜单中的“添加功能”  命令。 可使用“功能设计器”查看或更改功能的内容。 有关详细信息，请参阅 [如何︰ 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。

 当将某个功能添加到 SharePoint 项目时，此功能会作为节点显示在“解决方案资源管理器”  中，默认名称为 Feature*x*.feature，其中的 *x* 是唯一的编号。 将某个功能部署到 SharePoint Server 后，SharePoint 管理员可以将其激活，使其可用于 SharePoint 站点用户。

#### <a name="package-node"></a>包节点
 “包”  节点只包含一个作为 SharePoint 项目分发机制的文件。 此文件中，称为 *解决方案**包*, ，是。CAB\-具有基于。WSP 扩展。 解决方案包是一种可部署的且可重用的文件，其中包含一组可应用于 SharePoint 站点的并且可以单独启用或禁用的功能、站点定义和程序集。 ”包“  节点也始终包含名为 Package.wspdef 的文件，此文件是该包的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 定义文件。 一旦将包部署到运行 SharePoint 的服务器，SharePoint 管理员就可以对其进行安装并激活其功能。

 您可以查看或更改包的内容在包设计器或者通过双击\-单击包节点或通过打开其快捷菜单，然后选择 **打开**。 有关详细信息，请参阅 [创建 SharePoint 解决方案包](../sharepoint/creating-sharepoint-solution-packages.md)。

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint 项目和项目项属性
 与其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目一样，SharePoint 项目在“属性”窗口和“属性”页中显示属性。 显示的属性取决于所选择的节点。

 当在“解决方案资源管理器” 中选择 SharePoint 项目、项目项或项目项文件节点时，将在“属性”窗口或“属性”页显示以下属性：

### <a name="project-properties"></a>项目属性

|属性名|说明|
|-------------------|-----------------|
|活动部署配置|指定部署过程中执行的步骤序列。 有关详细信息，请参阅 [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。|
|程序集部署目标|确定 *SharePoint 应用程序程序集* 的所在位置。 有效的程序集位置值为 *GlobalAssemblyCache* \(默认\), ，或 *WebApplication*。<br /><br /> 如果将 *Sandboxed Solution* 属性设置为 **true**，则禁用此属性。|
|自动\-调试后收回|指定部署的解决方案是否在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中的调试模式下运行应用程序后自动从 SharePoint 收回。 当选中时，该解决方案会在调试后 IDE 返回设计视图时收回。 当取消选中时，该解决方案不会收回。 有关详细信息，请参阅 [收回解决方案](http://go.microsoft.com/fwlink/?LinkId=183819)。|
|编辑配置|指定要用于该项目的部署配置。 有关详细信息，请参阅 [如何︰ 编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 和 [部署、 发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。|
|启用 Silverlight 调试 \(而不是脚本调试\)|当选中时，Silverlight 调试器将附加到调试过程中。 当取消选中时，Script 调试器将附加到调试过程中。 有关详细信息，请参阅 [Silverlight 调试概述](http://go.microsoft.com/fwlink/?LinkId=179826)。|
|将程序集包含在包中|指定是否在生成时打包项目程序集。|
|开机自检\-部署命令行|指定在部署 SharePoint 解决方案后运行的命令。 此命令行支持任何批处理命令和 MSBuild 变量的分辨率。 有关详细信息，请参阅 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。|
|Pre\-部署命令行|指定在部署 SharePoint 解决方案之前运行的命令。 此命令行支持任何批处理命令和 MSBuild 变量的分辨率。 有关详细信息，请参阅 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)。|
|项目文件|包含有关项目的生成、配置和其他信息的文件的名称。|
|项目文件夹|系统中项目文件的位置。 \(读取\-仅。\)|
|Sandboxed Solution|指定是否应将项目部署为 *沙盒解决方案*, ，也称为 *用户\-创建解决方案*。 沙盒解决方案不一定是值得信任的。 **true** 的值表示将项目部署为沙盒解决方案，而 **false** 的值则表示将项目部署为场解决方案。 有关详细信息，请参阅 [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) 和 [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。|
|站点 URL|为此项目指定目标站点的 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 。|
|启动项|指定项目中的第一项运行。|

 当选择 SharePoint 项文件 \(如工作流或功能节点中的一个功能\), ，在属性窗口中将显示以下属性︰

### <a name="project-item-properties"></a>项目项属性

|属性名|说明|
|-------------------|-----------------|
|部署冲突解决方法|指定在要部署的项目项的属性与服务器上已有项的属性相同时，要执行的操作。 有关详细信息，请参阅 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。|
|功能属性|指定一组值 \(以密钥形式存储\/值对\) 部署到 SharePoint 时，这是包含一项功能。 部署功能后，可在代码中访问属性值。 有关详细信息，请参阅 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|功能接收器|提供在项目项包含的功能中发生特定事件时执行的代码。 有关详细信息，请参阅 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|文件夹名|SharePoint 项目项文件夹的名称。|
|项目输出引用|指定项目项运行所需的程序集等依赖项。 有关详细信息，请参阅 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|安全控件项|指定可以让不受信任的用户安全编辑的控件。 有关详细信息，请参阅 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|

### <a name="project-item-file-properties"></a>项目项文件属性

|属性名|说明|
|-------------------|-----------------|
|生成操作|指定文件与生成和部署过程的关系。 有关详细信息，请参阅 [文件属性](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)。|
|复制到输出目录|指定是否源文件\(s\) 将被复制到输出目录。 可以是以下值之一：<br /><br /> -   *请不要复制*<br />-   *始终复制*<br />-   *如果较新则复制*<br /><br /> 有关详细信息，请参阅 [文件属性](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)。|
|自定义工具|指定在设计时转换文件并将转换输出放置到另一个文件的工具的名称（如果有）。 例如，数据集 \(。[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]\) 文件具有一个默认的自定义工具。 有关详细信息，请参阅 [文件属性](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)。|
|自定义工具命名空间|用于复制自定义工具的输出的命名空间。 有关详细信息，请参阅 [文件属性](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)。|
|部署位置|完全\-限定的 SharePoint 服务器上的文件的路径。 此路径由部署根和部署路径子例程的\-属性。|
|部署路径|SharePoint Server 文件，例如 Workflow1 上的文件的相对路径\\。 完全\-限定的文件路径创建通过串联 *部署路径* 值到结束 *部署根* 值。<br /><br /> 选择的值 *RootFile* 为 *部署类型* 属性更改 *部署根* 属性设置为 {SharePointRoot}\\, ，从而导致完全\-限定的路径 {SharePointRoot}\\Workflow1\\。 有关详细信息，请参阅 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)。|
|Deployment Root|字符串。 将文件部署到 SharePoint Server 中的根文件夹。 例如，{SharePointRoot}\\模板\\功能\\{FeatureName}\\。<br /><br /> *Deployment Type* 设置决定 *Deployment Root* 属性的值。|
|RootFile|文件的部署类型，可决定 *Deployment Root* 值。 可以是以下值之一：<br /><br /> NoDeployment: \<没有值\><br /><br /> ElementManifest: {SharePointRoot}\\模板\\功能\\{FeatureName}\\<br /><br /> ElementFile: {SharePointRoot}\\模板\\功能\\{FeatureName}\\<br /><br /> TemplateFile: {SharePointRoot}\\模板\\<br /><br /> RootFile: {SharePointRoot}\\<br /><br /> GlobalResource: {SharePointRoot}\\资源\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> 有关详细信息，请参阅 <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>。|
|文件名|项文件的文件或文件夹名称|
|完整路径|项的文件的位置。 \(读取\-仅。\)|

## <a name="related-topics"></a>相关主题

|标题|描述|
|-----------|-----------------|
|[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)|描述在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中可用的 SharePoint 项目和项目项模板。|
|[如何︰ 向 SharePoint 项目添加项](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|描述如何将新项或现有项添加到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中。|
|[演练︰ 创建网站栏、 内容类型和 SharePoint 列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|单步的主管\-通过\-步骤中创建客户字段、 内容类型、 列表定义和列表实例。|
|[如何︰ 创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)|描述如何添加中创建的项目的事件接收器 [演练︰ 创建网站栏、 内容类型和列表的 sharepoint '](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。|
|[创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)|描述如何创建包括工作流关联窗体和工作流启动窗体的工作流项目。|
|[为 SharePoint 创建页](../sharepoint/creating-pages-for-sharepoint.md)|描述如何为 SharePoint 创建页（如应用程序页、网站页、母版页和页面布局）。|
|[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)|描述如何添加能够让用户借助浏览器便可直接修改 SharePoint 网站页的内容、外观和行为的控件。|
|[为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|描述如何创建可由 SharePoint 中运行的应用程序页和 Web 部件使用的用户控件。|
|[将业务数据集成到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|描述如何将数据从 Web 服务集成的来回\-结束到 SharePoint 应用程序的服务器应用程序。|
|[创建 SharePoint 网站定义](../sharepoint/creating-site-definitions-for-sharepoint.md)|描述如何创建站点定义：用于创建 SharePoint 站点的模板。|
|[从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|描述如何从现有的 SharePoint 站点将项（如内容类型和模块）导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目。|
|[使用模块包括解决方案中的文件](../sharepoint/using-modules-to-include-files-in-the-solution.md)|描述如何使用模块将文件从 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目部署到 SharePoint 站点。|
|[使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|描述如何通过使用服务器资源管理器浏览本地 SharePoint 站点。|
|[提供打包和部署在项目项中的信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|描述如何使用项目项属性提供项目的打包和部署信息，如安全控件项、项目输出引用和功能属性。|
|[如何︰ 添加和移除映射的文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)|描述如何将映射的文件夹添加到项目以便更容易访问 SharePoint 资源。|
|[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)|描述与沙盒解决方案相关联的问题。|
|[SharePoint 解决方案的安全性](../sharepoint/security-for-sharepoint-solutions.md)|描述有关在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中开发 SharePoint 解决方案的安全注意事项。|
|[URL 选取器对话框 &#40;在 Visual Studio &#41; 中的 SharePoint 开发](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|描述将路径引用添加到项目中或在本地 SharePoint 服务器上所使用的对话框。|

## <a name="see-also"></a>另请参阅
 [入门教程 &#40;在 Visual Studio &#41; 中的 SharePoint 开发](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md) 
 [使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md) 
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md) 
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

  