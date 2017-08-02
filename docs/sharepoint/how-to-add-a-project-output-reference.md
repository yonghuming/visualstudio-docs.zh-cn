---
title: "如何：添加项目输出引用"
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
  - "项目输出引用 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 高级打包工具"
  - "Visual Studio 中的 SharePoint 开发, 项目输出引用"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：添加项目输出引用
  若要将非 SharePoint 项目程序集（或 Silverlight 项目中的 .xap 文件）部署到 SharePoint，请将它们作为项目输出引用添加。  
  
 此过程将在两个项目之间创建一个解决方案生成依赖项。  在生成和部署 SharePoint 项目之前，将生成与项目输出引用关联的项目。  
  
### 添加项目输出引用  
  
1.  加载至少包含一个 SharePoint 项目和一个非 SharePoint 项目的解决方案。  
  
2.  在**“解决方案资源管理器”**中，选择 SharePoint 项目节点的项。  
  
3.  在**“属性”**窗口中，选择**“项目输出引用”**属性，然后选择该属性旁边的省略号 \(![ASP.NET 移动设计器中的省略号](~/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\) 按钮。  
  
4.  在**“项目输出引用”**对话框中，选择**“添加”**按钮。  
  
5.  在属性窗格中，选择**“部署类型”**属性旁边的箭头，并为所引用的非 SharePoint 项选择适当的值，例如**“ElementFile”**。  
  
6.  选择 **项目名称**旁边的箭头，并选择非 SharePoint 项目项的名称，然后选择 **确定** 按钮。  
  
## 请参阅  
 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [如何：将控件标记为安全控件](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  