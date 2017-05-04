---
title: "如何：创建事件接收器 | Microsoft Docs"
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
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "事件接收器 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 事件接收器"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：创建事件接收器
  通过创建 *事件接收器*，当用户与 SharePoint 项交互\(如列表或列表项）时，您可以回应。  例如当用户更改日历或从联系人列表中删除某个姓名时，将会触发事件接收器中的代码。  通过以下主题，您可以学习如何将事件接收器添加到列表实例中。  
  
 若要完成这些步骤，您必须安装 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和支持的 Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  由于此示例需要 SharePoint 项目，您还必须完成 [演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)主题中的过程。  
  
## 添加事件接收器  
 在 [演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 创建的项目包含自定义网站栏、自定义列表和的内容类型。  在下面的过程中，您将通过添加一个简单的事件处理程序 \(事件接收器\) 添加到列表实例项目，展开此演示如何在 SharePoint 项 （如列表中）发生的事件。  
  
#### 向列表实例中添加事件接收器  
  
1.  打开在[演练：创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)中创建的项目。  
  
2.  在 **解决方案资源管理器**中，选择的 SharePoint 项目节点，名为 **诊所**。  
  
3.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
4.  在**“Visual C\#”**或**“Visual Basic”**下，展开**“SharePoint”**节点，然后选择**“2010”**项。  
  
5.  在 **模板** 窗格中，选择 **事件接收器**，将其命名为 TestEventReceiver1，然后选择 **确定** 按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
6.  在**“需要哪种类型的事件接收器?”**列表中，选择**“列表项事件”**。  
  
7.  在 **哪个项应为事件源？** 列表中，选择 **Patients \(Clinic\\Patients\)**。  
  
8.  在**要处理的事件**的列表中，选中**“已添加项”**旁边的复选框，然后单击**“完成”**按钮。  
  
     新的事件接收器代码文件包含一个名为 `ItemAdded` 的方法。  在下一步中，将代码添加到此方法中，以便每个联系人默认命名为" Scott Brown "。  
  
9. 用下面的代码替换现有的 `ItemAdded` 方法，然后选择F5键。  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     运行代码，并在 Web 浏览器中查看 SharePoint 网站。  
  
10. 在快速启动栏上，选择 **Patients** 链接，然后选择 **添加新项** 链接。  
  
     新的输入窗体将打开。  
  
11. 在字段中输入数据，然后选择 **保存** 按钮。  
  
     在选择 **保存** 按钮之后，**Patient Name** 列名称自动更新为" Scott Brown "。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  