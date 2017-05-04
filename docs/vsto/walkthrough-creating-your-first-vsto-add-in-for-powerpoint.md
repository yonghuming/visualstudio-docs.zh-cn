---
title: "演练：创建你的第一个 PowerPoint VSTO 外接程序 | Microsoft Docs"
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
  - "外接程序 [Visual Studio 中的 Office 开发], 创建您的第一个项目"
  - "应用程序级外接程序 [Visual Studio 中的 Office 开发], 创建您的第一个项目"
  - "Visual Studio 中的 Office 开发, 创建您的第一个项目"
  - "PowerPoint [Visual Studio 中的 Office 开发], 创建您的第一个项目"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 演练：创建你的第一个 PowerPoint VSTO 外接程序
  本演练显示如何为 Microsoft Office PowerPoint 创建 VSTO 外接程序。  你在此类解决方案中创建的功能可用于应用程序本身，而与所打开的演示文稿无关。  有关详细信息，请参阅 [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 本演练阐释了以下任务：  
  
-   创建 PowerPoint 的 PowerPoint VSTO 外接程序。  
  
-   编写使用 PowerPoint 对象模型来将文本框添加到每张新建幻灯片的代码。  
  
-   生成并运行项目，以对其进行测试。  
  
-   清理项目，使 VSTO 外接程序在开发计算机上不再自动运行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## 创建项目  
  
#### 创建新项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后单击**“项目”**。  
  
3.  在模板窗格中，展开**“Visual C\#”**或**“Visual Basic”**，然后展开**“Office\/SharePoint”**。  
  
4.  在展开的**“Office\/SharePoint”**节点下方，选择**“Office 外接程序”**节点。  
  
5.  在项目模板列表中，选择一个 PowerPoint VSTO 外接程序项目。  
  
6.  在**“名称”**框中，键入 **FirstPowerPointAddIn**。  
  
7.  单击“确定”。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 即会创建 **FirstPowerPointAddIn** 项目，并在编辑器中打开 **ThisAddIn** 代码文件。  
  
## 编写将文本添加到每张新建幻灯片的代码  
 接下来，将代码添加到 ThisAddIn 代码文件。  新代码将使用 PowerPoint 对象模型来将文本框添加到每张新建幻灯片。  默认情况下，ThisAddIn 代码文件包含以下生成的代码：  
  
-   `ThisAddIn` 类的部分定义。  此类提供代码的入口点，并提供对 PowerPoint 对象模型的访问权限。  有关详细信息，请参阅 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  `ThisAddIn` 类的其余部分是在隐藏代码文件中定义的，不应修改该代码文件。  
  
-   `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件处理程序。  PowerPoint 加载和卸载 VSTO 外接程序时会调用这些事件处理程序。  使用这些事件处理程序，可在加载 VSTO 外接程序对其进行初始化，并在卸载 VSTO 外接程序时清理其使用的资源。  有关详细信息，请参阅 [Office 项目中的事件](../vsto/events-in-office-projects.md)。  
  
#### 若要将文本框添加到每张新建幻灯片中  
  
1.  在 ThisAddIn 代码文件中，将下面的代码添加到 `ThisAddIn` 类中。  此代码定义了 <xref:Microsoft.Office.Interop.PowerPoint.Application> 对象的 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件的一个事件处理程序。  
  
     当用户将新的幻灯片添加到活动演示文稿中时，此事件处理程序会将文本框添加到该新幻灯片的顶部，并添加文本到文本框中。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  如果你使用的是 C\#，请将以下代码添加到 `ThisAddIn_Startup` 事件处理程序中。  需要此代码将 `Application_PresentationNewSlide` 事件处理程序与 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件连接在一起。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 若要修改每张新建幻灯片，之前的代码示例需使用以下对象：  
  
-   `ThisAddIn` 类的 `Application` 字段。  `Application` 字段返回一个 <xref:Microsoft.Office.Interop.PowerPoint.Application> 对象，该对象表示 PowerPoint 的当前实例。  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件的事件处理程序的 `Sld` 参数。  `Sld` 参数是一个 <xref:Microsoft.Office.Interop.PowerPoint.Slide> 对象，用于表示新幻灯片。  有关详细信息，请参阅 [PowerPoint 解决方案](../vsto/powerpoint-solutions.md)。  
  
## 测试项目  
 当生成和运行项目时，请验证添加到演示文稿的新幻灯片中是否出现文本框。  
  
#### 测试项目  
  
1.  按 **F5** 生成并运行项目。  
  
     生成项目时，会将代码编译成一个程序集，此程序集放置在项目的生成输出文件夹中。  Visual Studio 还会创建一组注册表项，通过这些注册表项，PowerPoint 能够发现和加载 VSTO 外接程序，Visual Studio 还将开发计算机上的安全设置配置为允许 VSTO 外接程序运行。  有关详细信息，请参阅 [生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
2.  在 PowerPoint 中，将新的幻灯片添加到活动演示文稿。  
  
3.  验证下面的文本是否添加到幻灯片顶部的新建文本框中。  
  
     **此文本是通过使用代码添加的。**  
  
4.  关闭 PowerPoint。  
  
## 清理项目  
 完成项目开发后，请从开发计算机上删除 VSTO 外接程序程序集、注册表项和安全设置。  否则，每次在开发计算机上打开 PowerPoint 时 VSTO 外接程序都会运行。  
  
#### 清理项目  
  
1.  在 Visual Studio 中，在**“生成”**菜单上，单击**“清理解决方案”**。  
  
## 后续步骤  
 既然已经创建了一个基本的 PowerPoint VSTO 外接程序，就可以从下面这些主题中了解有关如何开发 VSTO 外接程序的详细信息：  
  
-   可在 PowerPoint 的 VSTO 外接程序中执行的常规编程任务。  有关详细信息，请参阅 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)。  
  
-   使用 PowerPoint 对象模型。  有关详细信息，请参阅 [PowerPoint 解决方案](../vsto/powerpoint-solutions.md)。  
  
-   自定义 PowerPoint 的 UI，例如通过将自定义选项卡添加到功能区或创建你自己的自定义任务窗格。  有关详细信息，请参阅 [Office UI 自定义](../vsto/office-ui-customization.md)。  
  
-   生成和调试 PowerPoint VSTO 外接程序。  有关详细信息，请参阅[生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
-   部署 PowerPoint VSTO 外接程序。  有关详细信息，请参阅[部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。  
  
## 请参阅  
 [VSTO 外接程序编程](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint 解决方案](../vsto/powerpoint-solutions.md)   
 [Office UI 自定义](../vsto/office-ui-customization.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [Office 项目模板概述](../vsto/office-project-templates-overview.md)  
  
  