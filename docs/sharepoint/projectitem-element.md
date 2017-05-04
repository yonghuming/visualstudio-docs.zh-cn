---
title: "ProjectItem Element | Microsoft Docs"
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
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  表示 SharePoint 项目项。  这是 .spdata 文件的必需的根元素。  
  
## 语法  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|**DefaultFile**|可选的 **xs:string** 特性。<br /><br /> 在您于**“解决方案资源管理器”**中打开 SharePoint 项目项时，Visual Studio 编辑器中打开的文件的相对路径（包括文件名）。  路径与包含 .spdata 文件的文件夹是相对的。|  
|**FeatureReceiverClass**|可选的 **xs:string** 特性。<br /><br /> 功能接收器类完全合格的名称，用于该 SharePoint 项目项。  有关功能接收器的更多信息，请参见[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|  
|**FeatureReceiverAssembly**|可选的 **xs:string** 特性。<br /><br /> 指定程序集完全合格的名称，其定义了该 SharePoint 项目项的接收器。  有关功能接收器的更多信息，请参见[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  有关完全限定程序集名称的更多信息，请参见 [程序集名称](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e)。|  
|**SupportedTrustLevels**|可选的 **xs:string** 特性。<br /><br /> 指定该 SharePoint 项目项支持的信任级别。  此值可以为以下字符串之一：Sandboxed、FullTrust 或 All。  值 All 指定 Sandboxed 和 FullTrust。<br /><br /> 在自定义的 SharePoint 项目项类型中，此特性的值对应于在实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法时分配给 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 属性的值。  如果您为此特性指定了一个不同的值，则 Visual Studio 将覆盖该值，以使其指定的信任级别与您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 属性中指定的信任级别相同。|  
|**SupportedDeploymentScopes**|可选的 **xs:string** 特性。<br /><br /> 指定该 SharePoint 项目项支持的部署范围。  此值是以逗号分隔的字符串，其组成为一个或多个下列字符串：服务器场、网站、Web、WebApplication 或程序包。  例如，"Web、站点"。<br /><br /> 在自定义的 SharePoint 项目项类型中，此特性的值对应于在实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法时分配给 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 属性的值。  如果您为此特性指定了一个不同的值，则 Visual Studio 将覆盖该值，以使其指定的信任级别与您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 属性中指定的信任级别相同。|  
|**Type**|必选的 **xs:string** 特性。<br /><br /> SharePoint 项目项的标识符。  在自定义 SharePoint 项目项类型时，标识符即是传递给 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的字符串。  有关更多信息，请参见[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。<br /><br /> 有关 Visual Studio 附带的内置 SharePoint 项目项的标识符，请参见[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|可选元素。<br /><br /> 表示与 SharePoint 项目项关联的自定义数据项的集合。<br /><br /> 只能包含一个 **ExtensionData** 元素。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|可选元素。<br /><br /> 表示将功能部署到 SharePoint 时功能附带的属性值的集合。<br /><br /> 只能包含一个 **FeatureProperties** 元素。|  
|[Files](../sharepoint/files-element.md)|可选的 **FileCollectionType** 元素。<br /><br /> 指定要用 SharePoint 项目项部署的文件，如功能元素文件和依赖于非 SharePoint 项目的输出。<br /><br /> 必须包含 **Files** 或 **ProjectItemFolder** 元素，但是不能同时包含二者。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|可选的 **ProjectItemFolderType** 元素。<br /><br /> 表示映射的文件夹。<br /><br /> 必须包含 **Files** 或 **ProjectItemFolder** 元素，但是不能同时包含二者。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|可选元素。<br /><br /> 表示 ASPX 控件或 Web 部件的集合，这些控件或部件已指定为安全，可供任何用户在 SharePoint 网站上的任何 ASPX 页上访问。<br /><br /> 只能包含一个 **SafeControls** 元素。|  
  
### 父元素  
 无。  
  
## 元素信息  
  
|||  
|-|-|  
|**命名空间**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**是否可以为空**|否|  
  
## 请参阅  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  