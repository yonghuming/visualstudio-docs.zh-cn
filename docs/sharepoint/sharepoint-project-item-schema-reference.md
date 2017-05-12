---
title: "SharePoint Project Item Schema Reference"
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
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio 使用 SharePoint 项目项架构来验证 .spdata 文件的内容。  .spdata 文件指定 SharePoint 项目项的内容和行为。  有关 SharePoint 项目项的内容的更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 SharePoint 项目项架构名为 ProjectItemModelSchema.xsd，默认情况下安装在 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas 中。  
  
 根元素为 [ProjectItem](../sharepoint/projectitem-element.md) 元素。  下表描述了该架构定义的所有元素。  
  
|元素|描述|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|表示与 SharePoint 项目项关联的自定义数据项的集合。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|表示与 SharePoint 项目项关联的自定义数据项（采用键\/值格式）。  键和值都必须为字符串。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示将功能部署到 SharePoint 时功能附带的属性值的集合。  部署功能之后，您可以在代码中访问属性值。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|表示将功能部署到 SharePoint 时功能附带的自定义属性。  部署功能之后，您可以在代码中访问属性。|  
|[Files](../sharepoint/files-element.md)|指定要随 SharePoint 项目项一起部署的文件，例如功能元素文件或项目的输出。|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|表示在将项目项部署到 SharePoint 时要随项目项一起附带的 SharePoint 文件，例如功能元素文件。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|表示映射的文件夹。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|表示在将项目项部署到 SharePoint 时要随项目项一起附带的项目的输出。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|表示一个 ASPX 控件或 Web 部件，该控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示 ASPX 控件或 Web 部件的集合，这些控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。|  
  
## 请参阅  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  