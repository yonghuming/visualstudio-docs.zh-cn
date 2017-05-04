---
title: "演练：部署项目任务列表定义 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发, 部署"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 演练：部署项目任务列表定义
  此演练演示如何使用 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 创建、自定义、调试和部署 SharePoint 列表定义以跟踪项目任务。  
  
 本演练阐释了以下任务：  
  
-   [创建 SharePoint 列表](#CreatingListDef)。  
  
-   [创建 SharePoint 列表](#CreatingListDef)。  
  
-   [添加事件接收器](#AddEventRcvr)。  
  
-   [自定义项目任务列表功能](#CustomizeFeature)。  
  
-   [生成和测试项目任务列表](#BuildTest)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]或 Visual Studio Application Lifecycle Management \(ALM\) 的某个版本。  
  
##  <a name="CreatingListDef"></a> 创建 SharePoint 列表  
 创建 SharePoint 列表项目，并将该列表定义与任务相关联。  
  
#### 创建 SharePoint 列表项目  
  
1.  打开**“新建项目”**对话框，再展开**“SharePoint”**节点，然后选择**“2010”**节点。  
  
2.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 模板，项目命名为 ProjectTaskList，然后选择 **确定** 按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
3.  指定用于调试的本地 SharePoint 网站，选择 **部署为场解决方案** 选项按钮，然后选择 **完成** 按钮。  
  
4.  打开该项目的快捷菜单，然后选择**“添加”**，**“新项目”**。  
  
5.  在**“模板”**窗格中，选择**“列表”**模板，然后选择**“添加”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
6.  在 **您想要对列表显示什么名称？** 框中，输入项目任务列表。  
  
7.  选择 **基于现有列表类型创建不可自定义的列表** 选项按钮，然后，在该列表中，选择 **任务**，然后选择 **完成** 按钮。  
  
     列表、功能和包显示在 **解决方案资源管理器**中。  
  
##  <a name="AddEventRcvr"></a> 添加事件接收器  
 在任务列表中，您可以添加自动设置任务的截止日期和说明的事件接收器。  下面的过程会将一个简单的事件处理程序作为事件接收器添加到列表实例中。  
  
#### 添加事件接收器  
  
1.  打开项目节点的快捷菜单，选择**“添加”**，然后选择 **“新项目”**。  
  
2.  在 SharePoint 模板列表中，选择**“事件接收器”**模板，并将其命名为 **ProjectTaskListEventReceiver**。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
3.  在 **选择事件接收器设置** 页上，选择 **列表项事件** 作为事件接收器类型，在 **您需要哪种类型的事件接收器** 输入列表。  
  
4.  在 **哪个项应为事件源** 列表中，选择 **任务**。  
  
5.  在要处理的事件的列表中，选中**“已添加项”**旁边的复选框，然后单击**“完成”**按钮。  
  
     新的事件接收器节点将添加到包含名为 **ProjectTaskListEventReceiver** 的代码文件的项目中。  
  
6.  向 **ProjectTaskListEventReceiver** 代码文件中的 `ItemAdded` 方法添加代码。  每当添加新任务时，就会向该任务添加默认截止日期和说明。  默认截止日期为 2009 年 7 月 1 日。  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> 自定义项目任务列表功能  
 在创建 SharePoint 解决方案时，Visual Studio 会自动为默认项目项创建功能。  您可以使用功能设计器来自定义 SharePoint 网站的项目任务列表设置。  
  
#### 自定义项目任务列表功能  
  
1.  在**“解决方案资源管理器”**中展开**“功能”**。  
  
2.  打开**“Feature1”**的快捷菜单，然后选择**“查看设计器”**。  
  
3.  在**“标题”**框中，键入**“项目任务列表功能”**。  
  
4.  在“范围”列表中，选择“网站”。  
  
5.  在**“属性”**窗口中，键入 **1.0.0.0** 作为**“Version”**属性的值。  
  
##  <a name="CustomizePackage"></a> 自定义项目任务列表包  
 在创建 SharePoint 项目时，Visual Studio 会自动向包中添加包含默认项目项的功能。  您可以使用包设计器来自定义 SharePoint 网站的项目任务列表设置。  
  
#### 自定义项目任务列表包  
  
1.  在**“解决方案”资源管理器**，打开**“包”**的快捷菜单，然后选择**“查看设计器”**。  
  
2.  在**“名称”**框中，输入 **“项目任务列表包”**。  
  
3.  选中**“重启Web服务器”**复选框。  
  
##  <a name="BuildTest"></a> 生成和测试项目任务列表  
 在运行项目时，SharePoint 网站将打开。  不过，您必须手动导航到任务列表的位置。  
  
#### 测试项目任务列表  
  
1.  选择 F5 以生成并部署项目任务列表。  
  
     SharePoint 网站将打开。  
  
2.  选择**“主页”**选项卡。  
  
3.  在左侧栏中，选择 **项目任务列表** 链接。  
  
     将显示“项目任务列表”页。  
  
4.  在 **列表工具** 选项卡，选择 **项** 选项卡。  
  
5.  在 **项** 组中，选择 **新建项** 按钮。  
  
6.  在**“标题”**文本框中，键入 Task1。  
  
7.  选择**保存**按钮。  
  
     刷新网站后，将显示**“任务 1”**任务，其截止日期为 7\/1\/2009。  
  
8.  选择**Task1**。  
  
     将显示任务的详细视图，并显示说明“这是一个关键任务”。  
  
##  <a name="Deploy"></a> 部署项目任务列表  
 生成并测试项目任务列表后，可以将它部署到本地系统或者远程系统。  本地系统是在其上开发解决方案的同一计算机，而远程系统是其他计算机。  
  
#### 将项目任务列表部署到本地系统  
  
1.  在 Visual Studio 菜单栏上选择 **生成**，**部署解决方案**。  
  
     Visual Studio 回收 IIS 应用程序池、收回解决方案的所有现有版本、将解决方案包 \(.wsp\) 文件复制到 SharePoint，然后激活其功能。  现在可以在 SharePoint 中使用该解决方案了。  有关部署配置步骤的更多信息，请参见[如何：编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
#### 将项目任务列表部署到远程系统  
  
1.  在 Visual Studio 菜单栏上，选择**“生成”**，再选择**“发布”**。  
  
2.  在 **发布** 对话框中，选择 **发布到文件系统** 选项按钮。  
  
     通过选择省略号按钮 ![“省略号”图标](../sharepoint/media/ellipsisicon.png "“省略号”图标") 将定位 **发布** 更改对话框的目标位置到另一个位置。  
  
3.  选择**“发布”**按钮。  
  
     .wsp 文件的创建解决方案。  
  
4.  将 .wsp 文件复制到远程 SharePoint 系统。  
  
5.  使用 PowerShell `Add-SPUserSolution` 命令在远程 SharePoint 安装上安装该程序包。（对于场解决方案，请使用 `Add-SPSolution` 命令。）  
  
     例如，`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`。  
  
6.  使用 PowerShell `Install-SPUserSolution` 命令部署解决方案。（对于场解决方案，请使用 `Install-SPSolution` 命令。）  
  
     例如，`Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`。  
  
     有关远程部署的更多信息，请 [使用解决方案](http://go.microsoft.com/fwlink/?LinkId=217680) 参见和 [添加和部署使用 PowerShell 在 SharePoint 2010 的解决方案](http://go.microsoft.com/fwlink/?LinkId=217682)。  
  
## 后续步骤  
 有关如何自定义和部署 SharePoint 解决方案的更多信息，请参见以下主题：  
  
-   [演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [SharePoint Server 2010 的 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  