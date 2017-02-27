---
title: "如何：指定 ClickOnce 脱机或联机安装模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 指定安装模式"
  - "ClickOnce 安装模式"
  - "安装模式"
  - "脱机应用程序"
  - "联机应用程序"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：指定 ClickOnce 脱机或联机安装模式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的 `Install Mode` 确定应用程序是脱机使用还是联机使用。  如果选择**“该应用程序只能联机使用”**，则用户必须能够访问 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 发布位置（网页或文件共享）才能运行该应用程序。  如果选择**“该应用程序也可以脱机使用”**，则应用程序向**“开始”**菜单和**“添加或删除程序”**对话框添加项；用户能够在未连接时运行该应用程序。  
  
 `Install Mode` 可在**“项目设计器”**的**“发布”**页中设置。  
  
 **注意** 使用发布向导也可以设置 `Install Mode`。  有关更多信息，请参见[如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
### 使 ClickOnce 应用程序只能联机使用  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  在**“安装模式和设置”**区域中，单击**“该应用程序只能联机使用”**选项按钮。  
  
### 使 ClickOnce 应用程序可以联机或脱机使用  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  在**“安装模式和设置”**区域中，单击**“该应用程序也可以脱机使用”**选项按钮。  
  
     安装后，应用程序向**“开始”**菜单和控制面板中的**“添加或删除程序”**添加项。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [选择 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)