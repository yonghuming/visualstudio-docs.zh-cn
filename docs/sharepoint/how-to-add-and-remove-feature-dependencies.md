---
title: "如何：添加和移除功能依赖项"
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
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 功能"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：添加和移除功能依赖项
  您的 SharePoint 功能可能依赖其他功能的功能或数据。  在此情况下，可以将其他功能标记为您的功能的依赖项。  这样一来，SharePoint Server 可以确保在激活您的功能之前激活依赖的功能。  
  
## 添加依赖项  
 可以在解决方案中添加其他功能作为依赖项。  这样一来，可以确保在安装您的功能之前已安装并激活所需功能。  
  
#### 为解决方案中的功能添加依赖项  
  
1.  打开功能设计器，展开**功能激活依赖项** 节点，然后选择 **添加** 按钮。  
  
2.  在 **添加功能激活依赖项** 对话框中，选择 **在解决方案中添加功能的依赖项** 选项按钮，选择要添加为依赖关系的功能标题，然后选择 **添加** 按钮。  
  
     您可通过选择 Ctrl 键来选择多个标题，添加多个功能。  
  
## 添加自定义依赖项  
 可以将 SharePoint Server 上已部署的功能添加为依赖项。  这样一来，SharePoint 激活过程会进行检查以确保在安装您的功能之前已激活所有依赖的功能。  
  
#### 按照功能 ID 添加依赖项  
  
1.  打开功能设计器，展开**功能激活依赖项** 节点，然后选择 **添加** 按钮。  
  
2.  在 **添加功能激活依赖项** 对话框中，选择 **添加自定义依赖项** 选项按钮。  
  
3.  在**“功能 ID”**文本框中，输入要标记为激活依赖项的功能的 GUID，然后选择**“添加”**按钮。  
  
## 编辑自定义依赖项  
 可以编辑先前添加的自定义依赖项。  然而，只能移除而不能编辑解决方案中包含的依赖功能。  
  
#### 更改解决方案中功能的依赖项  
  
1.  打开功能设计器，然后展开 **功能激活依赖项** 节点。  
  
2.  选择要编辑功能的名称，然后选择 **编辑** 按钮。  
  
3.  在 **编辑自定义功能激活依赖项** 对话框，更改标题，ID功能或说明，然后选择 **提交** 按钮。  
  
## 移除依赖项  
  
#### 移除解决方案中功能的依赖项  
  
1.  在功能设计器中，展开 **功能激活依赖项** 节点，选择要移除的功能的名称，然后选择 **移除** 按钮。  
  
## 请参阅  
 [创建 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)   
 [如何：自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何：在 SharePoint 功能中添加和移除项](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  