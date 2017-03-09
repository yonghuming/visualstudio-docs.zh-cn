---
title: "如何：创建 WCF 工作流服务应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：创建 WCF 工作流服务应用程序
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 工作流服务应用程序是在它们自身与客户端之间跨进程边界传递消息的分布式通信服务。服务端服务协定的实现是通过 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 中的工作流活动，以类似于 .NET Framework 3.5 中的旧工作流服务的方式基于声明完成的。  
  
### 创建 WCF 工作流服务应用程序  
  
1.  启动 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]。  
  
2.  在**“文件”**菜单上，指向**“新建”**，然后选择**“项目…”**。  
  
     此时将打开**“新建项目”**对话框。  
  
3.  在**“已安装的模板”**窗格中，根据您选择的语言从**“Visual C\#”**或**“Visual Basic”**组选择**“WCF”**或**“工作流”**。  
  
4.  在中间窗格中，选择**“WCF 工作流服务应用程序”**。  
  
5.  在**“名称”**框中，输入项目的描述性名称以便于识别。  
  
6.  在**“位置”**框中，输入要保存项目的目录，或者单击**“浏览”**以导航到该目录。  
  
7.  在**“解决方案”**框中，选择创建新解决方案，然后单击**“确定”**。  
  
    > [!NOTE]
    >  如果要向现有解决方案添加工作流控制台应用程序，请在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 打开该解决方案，在 **“解决方案资源管理器”** 右击该解决方案，然后选择 **“添加”**、**“新建项目…”** 以打开 **“新建项目”** 对话框。按照此过程中的上述步骤继续操作。  
  
8.  该项目模板将创建一个 XAML 格式的服务定义。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 打开设计视图，其中显示一个 <xref:System.Activities.Statements.Sequence> 活动，该活动包含一组 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活动。  
  
## 请参阅  
 [如何：创建活动](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [创建工作流项目](../workflow-designer/creating-a-workflow-project.md)