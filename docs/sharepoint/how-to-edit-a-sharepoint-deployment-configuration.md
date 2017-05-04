---
title: "如何：编辑 SharePoint 部署配置 | Microsoft Docs"
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
  - "VS.SharePointTools.Project.DeploymentConfig"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 部署"
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：编辑 SharePoint 部署配置
  可以创建一个部署配置，也可以修改现有的部署配置。  例如，可以运行单个步骤或更改部署过程中的步骤顺序。  由于无法更改内置配置和以编程方式添加的配置，因此您可能需要创建或修改部署配置。  
  
## 创建 SharePoint 部署配置  
  
#### 创建 SharePoint 部署配置  
  
1.  在**解决方案资源管理器**中，选择 SharePoint 项目，然后在菜单栏上，选择**项目**，*ProjectName* **属性**。  
  
2.  在 **SharePoint** 选项卡中，选择 **新建** 按钮。  
  
     将出现**“添加新部署配置”**对话框。  
  
3.  在**“名称”**文本框中，键入部署配置的名称。  
  
4.  在**“可用部署步骤”**窗格中，选择要添加到部署配置中的步骤，选择 \(**\>**\) 按钮，然后选择**确定** 按钮。  
  
    > [!NOTE]  
    >  如果您已配置预先部署命令或后期部署命令，则仅当您将这些步骤添加到自定义的部署配置中时，这些步骤才会运行。  
  
## 更改活动部署配置  
  
#### 更改活动部署配置  
  
1.  在**解决方案资源管理器**中，选择 SharePoint 项目，然后在菜单栏上，选择**项目**，*ProjectName* **属性**。  
  
2.  选择**“SharePoint”**选项卡。  
  
3.  在 **活动部署配置** 列表框，选择要使用的部署配置的名称。  
  
## 请参阅  
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  