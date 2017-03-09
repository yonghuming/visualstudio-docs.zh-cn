---
title: "如何：创建活动库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：创建活动库
自定义活动用于在工作流中对特定业务流程进行建模。通过 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的活动库模板，可使用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 直观地创建这种自定义活动。  
  
### 创建工作流活动库  
  
1.  启动 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后选择**“项目…”**。  
  
     此时将打开**“新建项目”**对话框。  
  
3.  在**“项目类型”**窗格中，根据您的首选语言从**“Visual C\#”**项目或**“Visual Basic”**组选择**“工作流”**。  
  
4.  在**“模板”**窗格中选择**“活动库”**。  
  
5.  在**“名称”**框中，键入项目的描述性名称以便于识别。  
  
6.  在**“位置”**框中，键入要保存项目的目录，或者单击**“浏览”**以导航到该目录。  
  
7.  在**“解决方案”**框中，键入解决方案的描述性名称，然后单击**“确定”**。  
  
    > [!NOTE]
    >  如果要向现有解决方案添加工作流控制台应用程序，请在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 打开该解决方案，在 **“解决方案资源管理器”** 右击该解决方案，然后选择 **“添加”**、**“新建项目…”** 以打开 **“新建项目”** 对话框。按照此过程中的上述步骤继续操作。  
  
8.  该项目模板将创建一个 XAML 格式的活动定义。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 将打开并显示自定义活动的画布。  
  
9. 将活动从**“工具箱”**拖到设计图面以使其包含在您的自定义活动中。  
  
    > [!CAUTION]
    >  自定义活动的主体中只能有一个子活动；但是，该子活动可以是一个复合活动，如 <xref:System.Activities.Statements.Sequence> 活动或 <xref:System.Activities.Statements.Flowchart> 活动。  
  
## 请参阅  
 [如何：创建活动](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [创建工作流项目](../workflow-designer/creating-a-workflow-project.md)