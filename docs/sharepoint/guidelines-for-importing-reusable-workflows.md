---
title: "有关导入可重用工作流的准则"
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
helpviewer_keywords: 
  - "导入项 [Visual Studio 中的 SharePoint 开发]"
  - "可重用工作流 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 导入项"
  - "Visual Studio 中的 SharePoint 开发, 可重用工作流"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 有关导入可重用工作流的准则
  若要导入在 SharePoint Designer 创建的可重用工作流，请使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的“导入可重用 SharePoint 2010 工作流”项目模板。  此模板导入一个声明性工作流（仅 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]），并将其转换成代码工作流。可使用 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 代码增强转换的代码工作流。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [演练：将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 但“导入可重用 SharePoint 2010 工作流”模板只能导入场解决方案。  若要将工作流部署为沙盒解决方案，请使用“导入 SharePoint 2010 解决方案包”模板将其导入。  但是，如果这样做，您无法将工作流转换为代码工作流，同样也不能对其进行修改。  
  
## 使用“导入可重用工作流”模板导入可重用工作流  
 如果使用“导入可重用 SharePoint 2010 工作流”模板导入可重用工作流，则您可以像运行或更改任何其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 解决方案一样来运行或更改此解决方案，只不过您可能必须手动修复某些项。  
  
### 导入任务窗体  
 “导入可重用 SharePoint 2010 工作流”项目模板将导入所有启动窗体和关联窗体，但仅导入一个任务窗体，因为代码工作流架构只允许一个任务窗体。  原始工作流解决方案中的任何其他任务窗体将置于**“解决方案资源管理器”**中的**“其他已导入文件”**文件夹中。  
  
## 使用“导入 SharePoint 2010 解决方案包”模板导入可重用工作流  
 如果使用“导入 SharePoint 2010 解决方案包”模板导入可重用工作流，您需要考虑下列问题：  
  
-   在导入工作流后，可以选择 F5 立即在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中部署并运行工作流。  但是，如果您对导入的解决方案中的工作流进行任何修改，则可能必须先手动修复项目中的元素，然后才能部署和运行工作流。  
  
-   由于此工作流是声明性的，因此无法向其添加代码。  若要将此工作流转换为代码工作流，您必须使用“导入可重用 SharePoint 2010 工作流”模板将其导入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  
  
-   尽管您可以在设计视图中编辑工作流设计器 \(.xoml\) 文件，但还是建议您在源视图中编辑此文件，因为工作流设计器会显示假错误。  
  
-   在工作流中进行的调试对声明性内容不起作用。  [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] 中设置的断点将不会命中。  
  
## 导入全局可重用工作流解决方案  
 无法使用“导入可重用 SharePoint 2010 工作流”模板导入全局可重用工作流。  若要导入全局可重用工作流，您必须将其转换为非全局可重用工作流或必须使用“导入 SharePoint 2010 解决方案包”模板。  
  
 若要转换此工作流，请在 SharePoint Designer 中创建全局可重用工作流的副本（通过打开此工作流然后选择**“另存为副本”**）。  然后使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的“导入可重用 SharePoint 2010 工作流”模板导入新的可重用工作流。  
  
 若要按原样导入全局可重用工作流，不作任何修饰，请使用“导入 SharePoint 2010 解决方案包”模板。  如果您使用此方法，此工作流不会转换为代码工作流，而仍为声明性工作流。  
  
## 请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [演练：将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  