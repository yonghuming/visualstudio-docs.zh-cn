---
title: "工作流中的窗体支持"
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
  - "Visual Studio 中的 SharePoint 开发, 工作流"
  - "工作流 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 工作流中的窗体支持
  可以在工作流中使用四种类型的窗体：关联、启动、任务和修改。  这些窗体类型可基于 ASPX 窗体或 InfoPath 窗体。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 为特定窗体提供的支持级别取决于多种因素，下表对这些因素进行了说明。  有关工作流窗体类型的更多信息，请参见 MSDN 网站中 [工作流窗体概述](http://go.microsoft.com/fwlink/?LinkId=185228) 。  
  
## XML 重构  
 将 ASPX 关联或启动窗体添加到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流项目项之后，只要更新该窗体名称或部署路径或者删除该窗体，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 就会自动重构工作流的 Elements.xml 文件中的 XML，以使引用该关联或启动窗体的特性保持同步。  但是，当在工作流中使用其他窗体类型（如任务或修改窗体）时，Elements.xml 文件不会重构。  
  
## 新 Visual Studio 工作流中的窗体支持  
 下表列出了 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 对于工作流中使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建的 ASPX 或 InfoPat 窗体上的不同窗体类型的支持。  
  
|窗体类型|使用 ASPX 窗体在 Visual Studio 中创建的工作流|使用 InfoPath 窗体在 Visual Studio 中创建的工作流|  
|----------|---------------------------------------|-------------------------------------------|  
|Association|-   可使用**“工作流关联窗体”**项模板将 ASPX 关联窗体添加到工作流中。<br />-   当添加、重命名或删除窗体时或者窗体的部署路径发生更改时，将重构工作流的 Elements.xml 文件。<br />-   有关详细信息，请参阅[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中没有 InfoPath 关联窗体模板。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 与 InfoPath Designer 之间没有集成。<br />-   工作流的 Elements.xml 文件不会重构。|  
|启动|-   可使用**“工作流启动窗体”**项模板将 ASPX 启动窗体添加到工作流中。<br />-   当添加、重命名或删除窗体时或者窗体的部署路径发生更改时，将重构工作流的 Elements.xml 文件。<br />-   有关详细信息，请参阅[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中没有 InfoPath 关联窗体模板。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 与 InfoPath Designer 之间没有集成。<br />-   工作流的 Elements.xml 文件不会重构。|  
|任务|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中未提供 ASPX 任务窗体模板。  必须创建应用程序页，然后向该页添加代码。<br />-   工作流的 Elements.xml 文件不会重构。<br />-   有关更多信息，请参见 [工作流任务窗体 \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中没有 InfoPath 任务窗体模板。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 与 InfoPath Designer 之间没有集成。<br />-   工作流的 Elements.xml 文件不会重构。|  
|修改|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中未提供 ASPX 修改窗体模板。  若要添加修改窗体，则必须创建应用程序页，然后向该页添加代码。<br />-   工作流的 Elements.xml 文件不会重构。  您必须根据需要手动编辑它。<br />-   有关更多信息，请参见 [修改工作流窗体 \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中没有 InfoPath 修改窗体模板。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 与 InfoPath Designer 之间没有集成。<br />-   工作流的 Elements.xml 文件不会重构。|  
  
## 导入的 SharePoint 可重用工作流中的窗体支持  
 下表列出了对于导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 可重用工作流中的 ASPX 或 InfoPat 窗体上的不同窗体类型的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 支持。  
  
|窗体类型|从 SharePoint Designer 导入 ASPX 窗体的可重用工作流|从 SharePoint Designer 导入 InfoPath 窗体的可重用工作流|  
|----------|---------------------------------------------|-------------------------------------------------|  
|Association|-   工作流的 Elements.xml 文件中引用了该窗体。<br />-   当重命名或删除该窗体时或者该窗体的部署路径发生更改时，将重构工作流的 Elements.xml 文件。|-   导入了该窗体，但未在工作流的 Elements.xml 文件中引用它。<br />-   工作流的 Elements.xml 文件不会重构。|  
|启动|-   工作流的 Elements.xml 文件中的工作流引用了该窗体。<br />-   当重命名或删除该窗体时或者该窗体的部署路径发生更改时，将重构工作流的 Elements.xml 文件。|-   导入了该窗体，但未在工作流的 Elements.xml 文件中引用它。<br />-   工作流的 Elements.xml 文件不会重构。 **Note:**  必须为此方案添加并更改规则和属性，然后此方案才能工作。|  
|任务|-   工作流的 Elements.xml 文件中引用了该窗体。<br />-   工作流的 Elements.xml 文件不会重构。|-   导入了该窗体，但未在工作流的 Elements.xml 文件中引用它。<br />-   工作流的 Elements.xml 文件不会重构。 **Note:**  必须为此方案添加并更改规则和属性，然后此方案才能工作。|  
|修改|不适用。  不能在 SharePoint Designer 中创建 ASPX 修改窗体。|不适用。  除内置的 SharePoint Server 工作流（在导出工作流时将不会包含在 .wsp 文件中）外，不能在 SharePoint Designer 中创建 InfoPath 修改窗体。|  
  
## 请参阅  
 [演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  