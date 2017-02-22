---
title: "如何：创建工作流控制台应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：创建工作流控制台应用程序
使用 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 可为执行系统或人工流程创建工作流。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供用于创建这些工作流的设计图面。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 可用于在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内创建工作流，也可集成到重新承载该设计器的其他应用程序。  
  
 本主题介绍如何使用 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 在控制台应用程序中创建工作流。  
  
### 创建工作流控制台应用程序  
  
1.  启动 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后选择**“项目…”**。  
  
     此时将打开**“新建项目”**对话框。  
  
3.  在**“已安装的模板”**窗格中，根据您的首选语言从**“Visual C\#”**或**“Visual Basic”**组选择**“工作流”**。  
  
4.  在中间窗格中，选择**“工作流控制台应用程序”**。  
  
5.  在**“名称”**框中，输入项目的描述性名称以便于识别。  
  
6.  在**“位置”**框中，输入要保存项目的目录，或者单击**“浏览”**以导航到该目录。  
  
7.  在**“解决方案”**框中，输入新解决方案的名称。单击**“确定”**创建应用程序。  
  
    > [!NOTE]
    >  如果要向现有解决方案添加工作流控制台应用程序，请在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 打开该解决方案，在 **“解决方案资源管理器”** 右击该解决方案，然后选择 **“添加”**、**“新建项目…”** 以打开 **“新建项目”** 对话框。按照此过程中的上述步骤继续操作。  
  
8.  该项目模板将在 XAML 中创建一个工作流定义并在源代码中创建控制台应用程序定义。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 将打开并显示所创建工作流的画布。  
  
9. 若要编写工作流，请将活动或其他工作流项从**工具箱**拖到工作流中的设计图面。  
  
## 请参阅  
 [创建工作流项目](../workflow-designer/creating-a-workflow-project.md)