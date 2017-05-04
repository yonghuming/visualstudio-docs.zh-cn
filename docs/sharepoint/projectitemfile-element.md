---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  表示在将项目项部署到 SharePoint 时要随项目项一起附带的 SharePoint 文件，例如功能元素文件。  
  
## 语法  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## 类型  
 **ProjectItemFileType**  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**Source**|必选的 **xs:string** 特性。<br /><br /> 要使用项目项部署的文件的名称。|  
|**Target**|可选的 **xs:string** 特性。<br /><br /> 将在 SharePoint 上部署文件的路径（相对于部署根文件夹）。  部署根文件夹取决于 **Type** 特性指定的部署类型。  如果未指定 **Target** 特性，则文件将部署到名称是在 **Source** 特性中指定的文件夹。<br /><br /> 有关更多信息，请参见 **Deployment Path** 的说明和[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePint 项目项的 **Deployment Root** 属性。|  
|**Type**|必选的 **xs:string** 特性。<br /><br /> 文件的部署类型。  有关可能值的更多信息，请参见[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 项目项的 **Deployment Type** 属性的说明。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[Files](../sharepoint/files-element.md)|指定部署到 SharePoint 时要与 SharePoint 项目项包含在一起的文件。|  
  
## 备注  
 **ProjectItemFile** 元素中通常引用的 SharePoint 文件包括功能元素文件 \(Elements.xml\)、列表定义的架构文件 \(Schema.xml\) 和 Web 部件的Web 部件定义文件的（.webpart）。  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  