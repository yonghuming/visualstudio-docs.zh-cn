---
title: "SafeControls Element | Microsoft Docs"
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
  - "SafeControls element"
ms.assetid: f5ffdbbe-cf85-4e5a-9d39-3cd4462f2a0e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControls Element
  表示 ASPX 控件或 Web 部件的集合，这些控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。  
  
## 语法  
  
```  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|可选元素。<br /><br /> 表示一个 ASPX 控件或 Web 部件，该控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。|  
  
## 备注  
 有关安全控件的更多信息，请参见[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  