---
title: "演练：创建你的第一个 Outlook VSTO 外接程序 | Microsoft Docs"
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
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发]，创建你的第一个项目"
  - "Visual Studio 中的 Office 开发，创建你的第一个项目"
  - "外接程序 [Visual Studio 中的 Office 开发]，创建你的第一个项目"
  - "Outlook [Visual Studio 中的 Office 开发]，创建你的第一个项目"
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 演练：创建你的第一个 Outlook VSTO 外接程序
  本演练显示如何为 Microsoft Office Outlook 创建 VSTO 外接程序。 在此类解决方案中创建的功能可用于应用程序本身，而与所打开的 Outlook 项无关。 有关详细信息，请参阅[Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 本演练阐释了以下任务：  
  
-   为 Outlook 创建 Outlook VSTO 外接程序项目。  
  
-   编写使用 Outlook 对象模型将文本添加到新建邮件的主题和正文的代码。  
  
-   生成并运行项目，以对其进行测试。  
  
-   清理已完成的项目，使 VSTO 外接程序在开发计算机上不再自动运行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## 创建项目  
  
#### 若要在 Visual Studio 中创建 Outlook 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后单击**“项目”**。  
  
3.  在模板窗格中，展开**“Visual C\#”**或**“Visual Basic”**，然后展开**“Office\/SharePoint”**。  
  
4.  在展开的**“Office\/SharePoint”**节点下方，选择**“Office 外接程序”**节点。  
  
5.  在项目模板列表中，选择一个 Outlook VSTO 外接程序项目。  
  
6.  在**“名称”**框中，键入 **FirstOutlookAddIn**。  
  
7.  单击“确定”。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 即会创建 **FirstExcelAddIn** 项目，并在编辑器中打开 **ThisAddIn** 代码文件。  
  
## 编写将文本添加到每封新建邮件的代码  
 接下来，将代码添加到 ThisAddIn 代码文件。 新代码将使用 Outlook 对象模型将文本添加到每封新建邮件。 默认情况下，ThisAddIn 代码文件包含以下生成的代码：  
  
-   `ThisAddIn` 类的部分定义。 此类提供代码的入口点，并提供对 Outlook 对象模型的访问权限。 有关更多信息，请参见[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。`ThisAddIn` 类的其余部分是在隐藏代码文件中定义的，不应修改该代码文件。  
  
-   `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件处理程序。 Outlook 加载和卸载 VSTO 外接程序时会调用这些事件处理程序。 使用这些事件处理程序，可在加载 VSTO 外接程序对其进行初始化，并在卸载 VSTO 外接程序时清理其使用的资源。 有关详细信息，请参阅[Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
#### 若要将文本添加到每封新建邮件的主题和正文  
  
1.  在 ThisAddIn 代码文件中，声明 `ThisAddIn` 类中一个名为 `inspectors` 的字段。`inspectors` 字段保留对当前 Outlook 实例中检查器窗口的集合的引用。 此引用可防止垃圾回收器释放包含 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件的事件处理程序的内存。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_OutlookAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  将 `ThisAddIn_Startup` 方法替换为以下代码。 此代码会将一个事件处理程序附加到 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookAddInTutorial#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#2)]  
  
3.  在 ThisAddIn 代码文件中，将下面的代码添加到 `ThisAddIn` 类中。 此代码定义 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件的一个事件处理程序。  
  
     当用户创建新邮件时，此事件处理程序会将文本添加到邮件的主题行和正文。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookAddInTutorial#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#3)]  
  
 若要修改每封新建邮件，之前的代码示例需使用以下对象：  
  
-   `ThisAddIn` 类的 `Application` 字段。`Application` 字段返回一个 <xref:Microsoft.Office.Interop.Outlook.Application> 对象，该对象表示 Outlook 的当前实例。  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件的事件处理程序的 `Inspector` 参数。`Inspector` 参数是一个 <xref:Microsoft.Office.Interop.Outlook.Inspector> 对象，该对象表示新建电子邮件的检查器窗口。 有关详细信息，请参阅[Outlook 解决方案](../vsto/outlook-solutions.md)。  
  
## 测试项目  
 当生成和运行项目时，验证文本是否出现在新建邮件的主题行和正文。  
  
#### 测试项目  
  
1.  按 **F5** 生成并运行项目。  
  
     生成项目时，代码会编译成一个程序集，此程序集包含在项目的生成输出文件夹中。 Visual Studio 还会创建一组注册表项，通过这些注册表项，Outlook 能够发现和加载 VSTO 外接程序，Visual Studio 还将开发计算机上的安全设置配置为允许 VSTO 外接程序运行。 有关详细信息，请参阅[Office Solution Build Process Overview](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)。  
  
2.  在 Outlook 中，创建新邮件。  
  
3.  验证是否将以下文本添加到了邮件的主题行和正文。  
  
     **This text was added by using code.**  
  
4.  关闭 Outlook。  
  
## 清理项目  
 完成项目开发后，请从开发计算机上删除 VSTO 外接程序程序集、注册表项和安全设置。 否则，每次在开发计算机上打开 Outlook 时 VSTO 外接程序都会运行。  
  
#### 清理项目  
  
1.  在 Visual Studio 中，在**“生成”**菜单上，单击**“清理解决方案”**。  
  
## 后续步骤  
 你已经创建了一个基本的 Outlook VSTO 外接程序，现在可以从下面这些主题中了解有关如何开发 VSTO 外接程序的详细信息：  
  
-   可通过使用 Outlook VSTO 外接程序执行的常规编程任务。 有关更多信息，请参见[VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  
  
-   使用 Outlook 对象模型。 有关详细信息，请参阅[Outlook 解决方案](../vsto/outlook-solutions.md)。  
  
-   自定义 Outlook 的 UI，例如，通过将自定义选项卡添加到功能区或创建你自己的自定义任务窗格。 有关详细信息，请参阅[Office UI 自定义](../vsto/office-ui-customization.md)。  
  
-   生成和调试 Outlook VSTO 外接程序。 有关详细信息，请参阅[生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
-   部署 Outlook VSTO 外接程序。 有关更多信息，请参见[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [Outlook 解决方案](../vsto/outlook-solutions.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [Office 项目模板概述](../vsto/office-project-templates-overview.md)  
  
  