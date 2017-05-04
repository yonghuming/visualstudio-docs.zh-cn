---
title: "如何：添加资源文件 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "资源文件 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 资源文件"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：添加资源文件
  用于添加资源文件的命令位于解决方案资源管理器中的解决方案节点和功能节点的快捷菜单上。  有关详细信息，请参阅[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
### 向 SharePoint 解决方案添加全局资源文件  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，打开 SharePoint 解决方案。  
  
2.  在**“解决方案资源管理器”**中，选择一个SharePoint的项目节点，然后在菜单栏上选择**“项目”“添加新项”**。  
  
3.  在**“添加新项”**对话框中，选择**“全局资源文件”**模板，然后选择**“添加”**按钮。  
  
    > [!NOTE]  
    >  “全局资源文件”项目项模板仅在选择“SharePoint”项目项时显示。  
  
4.  在**“添加资源”**对话框中，选择资源文件的区域性，如“英语（美国）”。  
  
     这一步将向解决方案中添加格式为 Resource*x*.区域性*culture.***.**resx（如 Resource1.en\-US.resx）的全局资源文件。  
  
5.  如果 **资源编辑器** 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中打开，请将资源添加到资源文件。  
  
### 向 SharePoint 功能添加功能资源文件  
  
1.  如果 SharePoint 解决方案尚不在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，打开解决方案。  
  
2.  在 **解决方案资源管理器**中，打开的快捷菜单 **功能** 节点下的功能的名称，然后选择 **添加功能资源**。  
  
     此步骤将一个资源文件以一定格式添加到功能中，*ResourceFileName***.***culture***.**.resx，如 Feature1.en\-US.resx。  
  
3.  如果 **资源编辑器** 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中打开，请将资源添加到资源文件。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  