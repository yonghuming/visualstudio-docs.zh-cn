---
title: "ProjectItem 元素 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: ProjectItem element
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a9f1ac258f6501aedb2fd89ce21514d785b25f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="projectitem-element"></a>ProjectItem 元素
  表示一个 SharePoint 项目项。 这是.spdata 文件的所需的根元素。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**DefaultFile**|可选**xs: string**属性。<br /><br /> 包括的文件名称，当你打开中的 SharePoint 项目项时，在 Visual Studio 编辑器中打开的文件的相对路径**解决方案资源管理器**。 该路径是相对从包含.spdata 文件的文件夹。|  
|**FeatureReceiverClass**|可选**xs: string**属性。<br /><br /> 此 SharePoint 项目项功能接收器类完全限定的名称。 有关功能接收器的详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|  
|**FeatureReceiverAssembly**|可选**xs: string**属性。<br /><br /> 指定定义功能接收器此 SharePoint 项目项的程序集的完全限定的名称。 有关功能接收器的详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。 有关完全限定程序集名称的详细信息，请参阅[程序集名称](/dotnet/framework/app-domains/assembly-names)。|  
|**SupportedTrustLevels**|可选**xs: string**属性。<br /><br /> 指定此 SharePoint 项目项支持的信任级别。 此值可以是下列字符串之一： 沙盒解决方案，FullTrust，或所有。 值所有指定 Sandboxed 和 FullTrust。<br /><br /> 在某个自定义 SharePoint 项目项类型，此属性的值对应于分配给值<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>属性的实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 如果指定此属性的不同值时，Visual Studio 将覆盖的值，以便指定要在指定的相同信任级别<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>属性。|  
|**SupportedDeploymentScopes**|可选**xs: string**属性。<br /><br /> 指定此 SharePoint 项目项支持的部署作用域。 此值是一个以逗号分隔的字符串组成的一个或多个以下字符串： 场、 站点、 Web、 web 应用程序或包。 例如，"Web，站点"。<br /><br /> 在某个自定义 SharePoint 项目项类型，此属性的值对应于分配给值<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>属性的实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 如果指定此属性的不同值时，Visual Studio 将覆盖的值，以便指定要在指定的相同信任级别<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>属性。|  
|**类型**|所需**xs: string**属性。<br /><br /> SharePoint 项目项的标识符。 在自定义 SharePoint 项目项类型中，标识符是字符串，将传递给<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 有关详细信息，请参阅[如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。<br /><br /> Visual Studio 附带的内置 SharePoint 项目项的标识符的列表，请参阅[扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|可选元素。<br /><br /> 表示自定义数据与 SharePoint 项目项关联的项的集合。<br /><br /> 你只能包含一个**ExtensionData**元素。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|可选元素。<br /><br /> 表示部署到 SharePoint 时所包含的一项功能的属性值的集合。<br /><br /> 你只能包含一个**FeatureProperties**元素。|  
|[文件](../sharepoint/files-element.md)|可选**FileCollectionType**元素。<br /><br /> 指定要部署使用 SharePoint 项目项，如功能元素文件和依赖的非 SharePoint 项目的输出的文件。<br /><br /> 你必须将**文件**或**ProjectItemFolder**元素，但不是两者。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|可选**ProjectItemFolderType**元素。<br /><br /> 表示映射的文件夹。<br /><br /> 你必须将**文件**或**ProjectItemFolder**元素，但不是两者。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|可选元素。<br /><br /> 表示 ASPX 控件和指定为安全的任何用户访问 SharePoint 站点上的任意 ASPX 页上的 Web 部件的集合。<br /><br /> 你只能包含一个**SafeControls**元素。|  
  
### <a name="parent-elements"></a>父元素  
 无。  
  
## <a name="element-information"></a>元素信息  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|No|  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  