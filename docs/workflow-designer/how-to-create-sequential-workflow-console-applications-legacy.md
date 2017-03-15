---
title: "如何：创建顺序工作流控制台应用程序（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "控制台应用程序, 顺序工作流"
  - "顺序工作流, 控制台应用程序"
  - "工作流, 控制台应用程序"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 如何：创建顺序工作流控制台应用程序（旧版）
按照这些步骤可使用 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 提供的旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 来创建顺序工作流控制台应用程序项目。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
### 创建顺序工作流控制台应用程序  
  
1.  启动 Visual Studio。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后选择**“项目”**。  
  
     此时将打开**“新建项目”**对话框。  
  
3.  在**“新建项目”**窗口顶部的下拉列表中选择**“.NET Framework 3.0”**选项或**“.NET Framework 3.5”**选项以访问旧设计器。  
  
    > [!NOTE]
    >  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的默认选项为**“.NET Framework 4”**。此选项用于创建面向 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序，并且不使用旧设计器。  
  
4.  在**“项目类型”**窗格中，选择“Visual C\#”项目或“Visual Basic”项目（位于**“其他语言”**下），然后选择**“工作流”**。  
  
5.  在**“模板”**窗格中，选择**“顺序工作流控制台应用程序”**。  
  
6.  在**“名称”**框中，输入项目的描述性名称以便于识别。  
  
7.  在**“位置”**框中，输入要保存项目的目录，或者单击**“浏览”**以导航到该目录。  
  
     Windows 窗体设计器将会打开并显示所创建项目的 Form1。  
  
8.  单击**“确定”**。  
  
     工作流设计器将会打开并显示所创建的顺序工作流的工作流设计图面。  
  
9. 将活动从**工具箱**拖到**“放置活动”**指定区域中的设计图面。  
  
## 请参阅  
 [创建旧版工作流项目](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/zh-cn/557bcb1f-a7ab-49f6-8df7-2706b7001301)