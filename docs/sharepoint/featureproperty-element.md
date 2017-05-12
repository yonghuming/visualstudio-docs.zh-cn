---
title: "FeatureProperty Element"
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
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  表示将功能部署到 SharePoint 时功能附带的自定义属性。  部署功能之后，您可以在代码中访问属性。  
  
## 语法  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**Key**|必选的 **xs:string** 特性。<br /><br /> 用于存储和检索属性值的键。  每个属性都必须有在功能中属于唯一的密钥。|  
|**Value**|必选的 **xs:string** 特性。<br /><br /> 属性值。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示将功能部署到 SharePoint 时功能附带的属性值的集合。|  
  
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
  
  