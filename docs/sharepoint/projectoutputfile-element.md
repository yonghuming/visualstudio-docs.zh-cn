---
title: "ProjectOutputFile Element"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  表示部署到 SharePoint 时要与项目项包含在一起的单独项目输出。  
  
## 语法  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## 类型  
 **ProjectOutputFileType**  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**ProjectId**|必选的 **xs:string** 特性。<br /><br /> 要包括的具有输出的依赖项目 GUID。  这对应于独立的项目文件中的 **ProjectGuid** 元素。|  
|**ProjectPath**|必选的 **xs:string** 特性。<br /><br /> 包括具有要包含的输出的依赖项目的项目文件名的相对路径。  此路径相对于 SharePoint 项目的根文件夹，其包含 SharePoint 项目项。|  
|**Target**|可选的 **xs:string** 特性。<br /><br /> 要在 SharePoint 服务器上部署依赖项目输出的路径（相对于部署根文件夹）。  部署根文件夹取决于 **Type** 特性指定的部署类型。<br /><br /> 有关更多信息，请参见 **Deployment Path** 的说明和[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePint 项目项的 **Deployment Root** 属性。|  
|**Type**|必选的 **xs:string** 特性。<br /><br /> 用于依赖项目的输出的部署类型。  有关可能值的更多信息，请参见[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 项目项的 **Deployment Type** 属性的说明。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[Files](../sharepoint/files-element.md)|指定部署到 SharePoint 时要与 SharePoint 项目项包含在一起的文件。|  
  
## 备注  
 使用 **ProjectOutputFile** 元素在 SharePoint 项目项的部署中包含项目输出。  可以指定不同的项目或包含项目项的同一项目。  有关更多信息，请参见 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
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
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  