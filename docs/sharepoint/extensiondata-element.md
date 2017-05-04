---
title: "ExtensionData Element | Microsoft Docs"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  表示与 SharePoint 项目项关联的自定义数据项的集合。  
  
## 语法  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|可选元素。<br /><br /> 表示与 SharePoint 项目项关联的自定义数据项（采用键\/值格式）。  键和值都必须为字符串。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。|  
  
## 备注  
 当通过使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 属性将自定义的数据与 SharePoint 项目项关联时，Visual Studio 将数据保存到项目项 .spdata 文件中的 **ExtensionData** 元素。  有关更多信息，请参见[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  