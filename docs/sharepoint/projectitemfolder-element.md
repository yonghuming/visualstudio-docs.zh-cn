---
title: "ProjectItemFolder Element"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  表示映射的文件夹。  
  
## 语法  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## 类型  
 **ProjectItemFolderType**  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**Target**|必选的 **xs:string** 特性。<br /><br /> SharePoint 安装中文件夹的路径，其为映射文件所对应的（相对于部署根文件夹）。  部署根文件夹取决于 **Type** 特性指定的部署类型。<br /><br /> 有关更多信息，请参见 **Deployment Path** 的说明和[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePint 项目项的 **Deployment Root** 属性。|  
|**Type**|必选的 **xs:string** 特性。<br /><br /> 映射的文件夹的部署类型。  有关可能值的更多信息，请参见[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 项目项的 **Deployment Type** 属性的说明。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。|  
  
## 备注  
 有关映射文件夹的更多信息，请参见[如何：添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [如何：添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  