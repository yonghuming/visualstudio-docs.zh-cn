---
title: "SafeControl Element"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  表示一个 ASPX 控件或 Web 部件，该控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。  
  
## 语法  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**Assembly**|可选的 **xs:string** 特性。<br /><br /> 在其中定义 ASPX 控件或 Web 部件名称的程序集的名称。  默认情况下，此特性使用程序集名称的 **$SharePoint.Project.AssemblyFullName$** 可替换参数。  有关更多信息，请参见[可替换参数](../sharepoint/replaceable-parameters.md)。|  
|**IsSafe**|可选的 **xs:boolean** 特性。<br /><br /> 指定对于不受信任的用户访问，安全 ASPX 控件或 Web 部件是否安全。|  
|**IsSafeAgainstScript**|可选的 **xs:boolean** 特性。<br /><br /> 指定不受信任的用户是否可以查看或编辑 ASPX 控件或 Web 部件的属性。|  
|**Name**|可选的 **xs:string** 特性。<br /><br /> 集合中该安全控制项的名称。|  
|**Namespace**|可选的 **xs:string** 特性。<br /><br /> ASPX 控件或 Web 部件的命名空间。|  
|**TypeName**|可选的 **xs:string** 特性。<br /><br /> ASPX 控件或 Web 部件的类型名称。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示 ASPX 控件或 Web 部件的集合，这些控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。|  
  
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
  
  