---
title: "FeatureProperties Element"
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
  - "FeatureProperties element"
ms.assetid: 89233274-a842-4f40-a81a-5548379f6f39
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# FeatureProperties Element
  表示将功能部署到 SharePoint 时功能附带的属性值的集合。  部署功能之后，您可以在代码中访问属性值。  
  
## 语法  
  
```  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|可选元素。<br /><br /> 表示自定义属性，格式为键\/值。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。|  
  
## 备注  
 有关功能属性的更多信息，请参见[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
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
  
  