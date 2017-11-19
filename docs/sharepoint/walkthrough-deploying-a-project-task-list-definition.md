---
title: "演练： 部署项目任务列表定义 |Microsoft 文档"
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
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a9f981db2b48c550e1312acf4f387a495a0386e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>演练：部署项目任务列表定义
  本演练演示如何使用 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 创建、自定义、调试和部署 SharePoint 列表以跟踪项目任务。  
  
 本演练阐释了以下任务：  
  
-   [创建 SharePoint 列表](#CreatingListDef)。  
  
-   [创建 SharePoint 列表](#CreatingListDef)。  
  
-   [添加事件接收器](#AddEventRcvr)。  
  
-   [自定义项目任务列表功能](#CustomizeFeature)。  
  
-   [生成和测试项目任务列表](#BuildTest)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]或某一版本的 Visual Studio 应用程序生命周期管理 (ALM)。  
  
##  <a name="CreatingListDef"></a>创建 SharePoint 列表  
 创建 SharePoint 列表项目，并将该列表定义与任务相关联。  
  
#### <a name="to-create-a-sharepoint-list-project"></a>创建 SharePoint 列表项目  
  
1.  打开**新项目**对话框框中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
2.  在**模板**窗格中，选择**SharePoint 2010 项目**模板，将项目**命名为 ProjectTaskList**，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
3.  指定用于调试，本地 SharePoint 站点选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮。  
  
4.  打开该项目的快捷菜单，然后选择**添加**，**新项**。  
  
5.  在**模板**窗格中，选择**列表**模板，然后选择**添加**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
6.  在**你想要列表的显示名称？**框中，输入**项目任务列表**。  
  
7.  选择**创建基于现有列表类型的非可自定义列表**选项按钮，，然后，在其列表中，选择**任务**，然后选择**完成**按钮。  
  
     列表、 功能和包显示在**解决方案资源管理器**。  
  
##  <a name="AddEventRcvr"></a>添加事件接收器  
 在任务列表中，可以添加自动设置任务的截止日期和说明的事件接收器。 以下过程作为事件接收器将一个简单的事件处理程序添加到列表实例。  
  
#### <a name="to-add-an-event-receiver"></a>若要添加事件接收器  
  
1.  打开项目节点的快捷菜单，选择**添加**，然后选择**新项**。  
  
2.  在 SharePoint 模板列表中，选择**事件接收器**模板，然后将其**ProjectTaskListEventReceiver**。  
  
     **SharePoint 自定义向导**显示。  
  
3.  上**选择事件接收器设置**页上，选择**列表项事件**作为事件接收器类型中**你想进行何种类型的事件接收器**列表。  
  
4.  在**哪个项应为事件源**列表中，选择**任务**。  
  
5.  在要处理的事件列表中，选中的复选框旁边**项已添加**，然后选择**完成**按钮。  
  
     名为的代码文件的新的事件接收器节点添加到项目**ProjectTaskListEventReceiver**。  
  
6.  将代码添加到`ItemAdded`中的方法**ProjectTaskListEventReceiver**代码文件。 每次添加一个新任务，默认截止日期和描述添加到任务。 默认截止日期为 2009 年 7 月 1 日。  
  
     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]  
  
##  <a name="CustomizeFeature"></a>自定义项目任务列表功能  
 当创建 SharePoint 解决方案时，Visual Studio 自动创建默认的功能项目项。 你可以使用功能设计器自定义 SharePoint 站点的项目任务列表设置。  
  
#### <a name="to-customize-the-project-task-list-feature"></a>若要自定义项目任务列表功能  
  
1.  在**解决方案资源管理器**，展开**功能**。  
  
2.  打开的快捷菜单**Feature1**，然后选择**视图设计器**。  
  
3.  在**标题**框中，输入**项目任务列表功能**。  
  
4.  在**作用域**列表中，选择**Web**。  
  
5.  在**属性**窗口中，输入**1.0.0.0**的值作为**版本**属性。  
  
##  <a name="CustomizePackage"></a>自定义项目任务列表包  
 在创建 SharePoint 项目时，Visual Studio 会自动添加到包的默认项目项包含的功能。 你可以使用包设计器自定义 SharePoint 站点的项目任务列表设置。  
  
#### <a name="to-customize-the-project-task-list-package"></a>若要自定义项目任务列表包  
  
1.  在**解决方案资源管理器**，打开快捷菜单**包**，然后选择**视图设计器**。  
  
2.  在**名称**框中，输入**ProjectTaskListPackage**。  
  
3.  选择**重置 Web 服务器**复选框。  
  
##  <a name="BuildTest"></a>生成和测试项目任务列表  
 运行项目时，会打开 SharePoint 站点。 但是，您必须手动导航到的任务列表的位置。  
  
#### <a name="to-test-the-project-task-list"></a>若要测试项目任务列表  
  
1.  选择 F5 以生成并部署项目任务列表。  
  
     打开 SharePoint 站点。  
  
2.  选择**主页**选项卡。  
  
3.  在左侧栏中，选择**项目任务列表**链接。  
  
     显示的项目任务列表页面。  
  
4.  在**列表工具**选项卡上，选择**项**选项卡。  
  
5.  在**项**组中，选择**新项**按钮。  
  
6.  在**标题**文本框中，输入**Task1**。  
  
7.  选择**保存**按钮。  
  
     刷新站点后， **Task1**将显示任务 2009 年 7 月 1 日到期日期。  
  
8.  选择**Task1**。  
  
     将显示任务的详细的视图，并显示说明"This is 的关键任务"。  
  
##  <a name="Deploy"></a>部署项目任务列表  
 生成和测试项目任务列表后，你可以将其部署到*本地系统*或*远程系统*。 本地系统是在其开发解决方案，在同一台计算机，而远程系统是另一台计算机。  
  
#### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>部署到本地的系统的项目任务列表  
  
1.  在 Visual Studio 菜单栏上，选择**生成**，**部署解决方案**。  
  
     Visual Studio 回收 IIS 应用程序池、 将收回解决方案的任何现有版本，将解决方案包 (.wsp) 文件复制到 SharePoint，然后激活其功能。 你现在可以在 SharePoint 中使用该解决方案。 有关部署的配置步骤的详细信息，请参阅[如何： 编辑 SharePoint 部署配置](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)。  
  
#### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>若要部署到远程系统的项目任务列表  
  
1.  在 Visual Studio 菜单栏上，选择**生成**，**发布**。  
  
2.  在**发布**对话框框中，选择**发布到文件系统**选项按钮。  
  
     你可以更改中的目标位置**发布**对话框中，通过选择省略号按钮![省略号图标](../sharepoint/media/ellipsisicon.gif "省略号图标")，然后导航到另一个位置。  
  
3.  选择**发布**按钮。  
  
     将为此解决方案创建 .wsp 文件。  
  
4.  将.wsp 文件复制到远程 SharePoint 系统。  
  
5.  使用 PowerShell`Add-SPUserSolution`命令以在远程 SharePoint 安装上安装包。 (对于场解决方案，请使用`Add-SPSolution`命令。)  
  
     例如 `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`。  
  
6.  使用 PowerShell`Install-SPUserSolution`命令以部署解决方案。 (对于场解决方案，请使用`Install-SPSolution`命令。)  
  
     例如 `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`。  
  
     有关远程部署的详细信息，请参阅[使用解决方案](http://go.microsoft.com/fwlink/?LinkId=217680)和[添加和部署解决方案与在 SharePoint 2010 中的 PowerShell](http://go.microsoft.com/fwlink/?LinkId=217682)。  
  
## <a name="next-steps"></a>后续步骤  
 你可以了解有关如何自定义和部署 SharePoint 解决方案从以下主题：  
  
-   [演练：创建 SharePoint 的站点栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell for SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## <a name="see-also"></a>另请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  