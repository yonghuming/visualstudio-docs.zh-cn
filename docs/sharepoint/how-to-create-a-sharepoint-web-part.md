---
title: "如何：创建 SharePoint Web 部件 | Microsoft Docs"
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
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 添加"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 创建"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：创建 SharePoint Web 部件
  通过添加 SharePoint项目的“ Web 部件” 项并编辑 Web 部件的代码或使用设计师，您可以创建并自定义 Web 部件。  有关详细信息，请参阅[如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
### 创建 SharePoint Web 部件  
  
1.  打开或创建一个 SharePoint 项目。  
  
     有关详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在“解决方案资源管理器”中选择 SharePoint 项目节点，然后选择“项目”、“添加新项”。  
  
3.  在“添加新项”对话框中，展开“SharePoint” 节点，然后选择“2010”节点。  
  
4.  在 SharePoint 模版列表中，选择“ Web 部件”。  
  
5.  在“名称”框中，指定 Web 部件名称，然后选中“添加”按钮。  
  
     Web 部件显示在“解决方案资源管理器”中。  有关 Web 部件包含的文件，请参见[为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)。  
  
6.  在“解决方案资源管理器”中，打开刚被创建的 Web 组件代码文件。  
  
     例如，如果 Web 部件的名称为 WebPart1，请打开 WebPart1.vb（在 Visual Basic 中）或 WebPart1.cs（在 C\# 中）。  
  
7.  在代码文件中，向 <xref:System.Web.UI.Control.CreateChildControls%2A> 方法添加控件。  
  
     有关示例，请参见[演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)。  
  
## 请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [演练：使用设计器为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  