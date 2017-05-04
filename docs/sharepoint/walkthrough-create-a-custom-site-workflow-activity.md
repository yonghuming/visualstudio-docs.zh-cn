---
title: "演练：创建自定义网站工作流活动 | Microsoft Docs"
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
  - "自定义工作流活动 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 自定义工作流活动"
  - "Visual Studio 中的 SharePoint 开发, 网站工作流"
  - "网站工作流 [Visual Studio 中的 SharePoint 开发]"
  - "工作流活动 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 演练：创建自定义网站工作流活动
  本演练演示如何使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 为网站级工作流创建自定义活动。（网站级工作流适用于整个网站，而不只是网站上的列表。）自定义活动会创建一个备份的公告列表，然后将公告列表中的内容复制到该列表中。  
  
 本演练将演示以下任务：  
  
-   创建网站级工作流。  
  
-   创建自定义工作流活动。  
  
-   创建和删除 SharePoint 列表。  
  
-   将项从一个列表复制到另一个列表。  
  
-   在快速启动栏上显示列表。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 创建网站工作流自定义活动项目  
 首先，创建一个用来包含和测试自定义工作流活动的项目。  
  
#### 创建网站工作流自定义活动项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**，以显示**“新建项目”**对话框。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
3.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 模板。  
  
4.  在**“名称”**框中，输入AnnouncementBackup，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
5.  在 **指定用于调试的网站和安全级别** 页中，选择 **部署为场解决方案** 选项按钮，然后选择 **完成** 按钮以接受默认站点和信任级别。  
  
     此步骤会将解决方案的信任级别设置为场解决方案（工作流项目的唯一可用选项）。  
  
6.  在**“解决方案资源管理器”**中，选择项目节点，然后在菜单栏上选择**“项目”**，再选择**“添加新项”**。  
  
7.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
8.  在 **模板** 窗格中，选择 **顺序工作流 \(仅场解决方案\)** 模板，然后选择 **添加** 按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
9. 在**“指定用于调试的工作流名称”**页上，接受默认名称 \(AnnouncementBackup \- Workflow1\)。  将工作流模板类型更改为**“网站工作流”**，然后选择**“下一步”**按钮。  
  
10. 选择**“完成”**按钮以接受剩余的默认设置。  
  
## 添加自定义工作流活动类  
 接下来，向项目中添加一个类以包含自定义工作流活动的代码。  
  
#### 添加自定义工作流活动类  
  
1.  在菜单栏上选择**“项目”“添加新项”**以显示**“添加新项”**对话框。  
  
2.  在**“已安装的模板”**树视图中，选择**“代码”**节点，然后在项目项模板列表中选择**“类”**模板。  使用默认名称 Class1。  选择**“添加”**按钮。  
  
3.  将 Class1 中的所有代码替换为：  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  保存项目，然后在菜单栏上选择**“生成”**，**“生成解决方案”**。  
  
     Class1 出现在 **工具箱** 中的自定义操作 **AnnouncementBackup 组件** 选项卡。  
  
## 向网站工作流中添加自定义活动  
 接下来，向工作流中添加一个活动以包含自定义代码。  
  
#### 向网站工作流中添加自定义活动  
  
1.  在设计视图中，在工作流设计器内打开 Workflow1。  
  
2.  从 **工具箱** 拖动的 Class1，以使它在 `onWorkflowActivated1` 活动下方，或者打开 Class1 中的快捷菜单，选择 **复制**，打开行快捷菜单在 `onWorkflowActivated1` 活动下方，然后选择 **粘贴**。  
  
3.  保存项目。  
  
## 测试网站工作流自定义活动  
 紧接着，运行项目并启动网站工作流。  自定义活动会创建一个备份的公告列表，然后将当前公告列表中的内容复制到该列表中。  在创建备份列表之前，代码还会检查是否已存在备份列表。  如果已存在备份列表，则会将其删除。  代码还会向 SharePoint 网站的快速启动栏上的新列表中添加链接。  
  
#### 测试网站工作流自定义活动  
  
1.  选择 F5 运行项目，并将其部署到 SharePoint。  
  
2.  在快速启动栏上，选择**“列表”**链接以显示 SharePoint 网站中可用的所有列表。  请注意，仅有一个名为**“公告”**的公告列表。  
  
3.  在 SharePoint 网页顶部，选择 **网站工作流** 链接。  
  
4.  在“启动新工作流”部分下，选择**AnnouncementBackup – Workflow1**的链接。  这将启动网站工作流，并运行自定义操作中的代码。  
  
5.  在快速启动栏上，选择 **公告备份** 链接。  请注意，**“公告”**列表中包含的所有公告已复制到此新列表中。  
  
## 请参阅  
 [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  