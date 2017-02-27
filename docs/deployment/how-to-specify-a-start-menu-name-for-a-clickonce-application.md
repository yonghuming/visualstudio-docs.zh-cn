---
title: "如何：指定 ClickOnce 应用程序的“开始”菜单名称 | Microsoft Docs"
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
  - "ClickOnce 部署, “开始”菜单名称"
  - "“开始”菜单名称"
  - "“开始”菜单资源名称"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：指定 ClickOnce 应用程序的“开始”菜单名称
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序安装为联机和脱机皆可使用，则会在**“开始”**菜单和**“添加或删除程序”**列表中添加一项。  默认情况下，显示名称与应用程序程序集名称相同，但您可以通过设置**“发布选项”**对话框中的**“产品名称”**来更改显示名称。  
  
 **“产品名称”**将显示在 publish.htm 页中；对于安装的脱机应用程序，它将是**“开始”**菜单中显示的名称，也将是**“添加\/删除程序”**中显示的名称。  
  
 **“发行者名称”**将显示在 publish.htm 页上的**“产品名称”**上方，对于安装的脱机应用程序，它也将是包含**“开始”**菜单中应用程序图标的文件夹的名称。  
  
 您可以在**“发布选项”**对话框中设置**“产品名称”**和**“发行者名称”**属性，通过**“项目设计器”**的**“发布”**页可打开此对话框。  
  
### 指定“开始”菜单中的名称  
  
1.  在**“解决方案资源管理器”**中选定一个项目，然后在**“项目”**菜单中单击**“属性”**。  
  
2.  单击**“发布”**选项卡。  
  
3.  单击**“选项”**按钮打开**“发布选项”**对话框。  
  
4.  单击**“说明”**。  
  
5.  在**“发布选项”**对话框中，在**“产品名称”**中输入要显示的名称。  
  
6.  可以选择在**“发行者名称”**中输入发行者名称。  
  
## 请参阅  
 [发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)   
 [如何：使用发布向导发布 ClickOnce 应用程序](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)