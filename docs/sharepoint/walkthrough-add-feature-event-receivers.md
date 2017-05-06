---
title: "演练：添加功能事件接收器"
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
  - "Visual Studio 中的 SharePoint 开发, 高级打包工具"
  - "Visual Studio 中的 SharePoint 开发, 事件接收器"
  - "Visual Studio 中的 SharePoint 开发, 功能事件接收器"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 演练：添加功能事件接收器
  功能事件接收器是在 SharePoint 中发生下列功能相关事件之一时执行的方法：  
  
-   安装功能。  
  
-   激活功能。  
  
-   停用功能。  
  
-   移除功能。  
  
 本演练演示如何将事件接收器添加到 SharePoint 项目的功能中。  本演练将演示以下任务：  
  
-   创建包含功能事件接收器的空项目。  
  
-   处理 **FeatureDeactivating** 方法。  
  
-   使用 SharePoint 项目对象模型将公告添加到“公告”列表中。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 创建功能事件接收器项目  
 首先，将创建一个项目来包含功能事件接收器。  
  
#### 创建包含功能事件接收器的项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**，以显示**“新建项目”**对话框。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
3.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 模板。  
  
     您为功能事件接收器将使用此项目类型，因为它们没有项目模板。  
  
4.  在**“名称”**框中，键入 FeatureEvtTest，然后选择**“确定”**按钮以显示**“SharePoint 自定义向导”**。  
  
5.  在**“指定用于调试的网站和安全级别”**页上，输入要将新自定义字段项添加到 SharePoint Server 网站的 URL，或者使用默认位置 \(http:\/\/\<*system name*\>\/\)。  
  
6.  在“此 SharePoint 解决方案的信任级别是什么?”部分中，选中“部署为场解决方案”选项按钮。  
  
     有关沙盒化解决方案与场解决方案的更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  选择 **完成** 按钮，然后请注意名为 Feature1 的功能将出现在 **功能** 节点下。  
  
## 向功能中添加事件接收器  
 接下来，将向功能中添加事件接收器，并添加在停用功能时执行的代码。  
  
#### 向功能中添加事件接收器  
  
1.  打开功能节点的快捷菜单，然后选择 **添加功能 \(F\)** 创建一项功能。  
  
2.  在 **功能** 节点下，打开 **Feature1**的快捷菜单，然后选择 **添加事件接收器 \(E\)** 向功能中添加事件接收器。  
  
     这将在 Feature1 下添加一个代码文件。  在这种情况下，将该文件命名为 Feature1.EventReceiver.cs 或 Feature1.EventReceiver.vb，具体取决于项目的开发语言。  
  
3.  如果项目位于 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]中，如果它已不存在，在事件接收器的顶部，添加以下代码：  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  事件接收器类中包含几个充当事件的注释掉的方法。  用以下代码替换 **FeatureDeactivating** 方法：  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## 测试功能事件接收器  
 接下来，将停用功能，以测试 **FeatureDeactivating** 方法是否向 SharePoint 公告列表中输出公告。  
  
#### 测试功能事件接收器  
  
1.  将项目的**“活动部署配置”**属性的值设置为**无激活**。  
  
     设置此属性可防止在 SharePoint 中激活功能，并且您可以调试功能事件接收器。  有关详细信息，请参阅[调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
2.  选择 **F5** 键运行项目，并将其部署到 SharePoint。  
  
3.  在 SharePoint 网页顶部，打开**“网站操作”**菜单，然后选择**“网站设置”**。  
  
4.  在**“网站设置”**页的**“网站操作”**部分下，选择**“管理网站功能”**链接。  
  
5.  在**“网站功能”**页中，选择**“FeatureEvtTest Feature1”**功能旁边的**“激活”**按钮。  
  
6.  在 **功能** 页，选择 **FeatureEvtTest Feature1** 功能旁边选择 **停用** 按钮，然后选择 **停用此功能** 以确认链接以停用功能。  
  
7.  选择**“主页”**按钮。  
  
     请注意，停用功能之后，一个公告将出现在**“公告”**列表中。  
  
## 请参阅  
 [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  