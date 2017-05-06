---
title: "Files Element"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  指定要用 SharePoint 项目项部署的文件，如功能元素文件和依赖于非 SharePoint 项目的输出。  
  
## 语法  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## 类型  
 **FileCollectionType**  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|可选的 **ProjectItemFileType** 元素。<br /><br /> 表示在将项目项部署到 SharePoint 时要随项目项一起附带的 SharePoint 文件，例如功能元素文件。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|可选的 **ProjectOutputFileType** 元素。<br /><br /> 表示在将项目项部署到 SharePoint 时要随项目项一起附带的项目的输出。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。|  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  