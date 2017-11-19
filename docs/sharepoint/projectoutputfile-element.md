---
title: "ProjectOutputFile 元素 |Microsoft 文档"
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
helpviewer_keywords: ProjectOutputFile element
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a397648dd81ead8134777c8b36982fa6b65b687b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 元素
  表示要部署到 SharePoint 项目项包含一个单独的项目的输出。  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>类型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**ProjectId**|所需**xs: string**属性。<br /><br /> 具有你想要包括的输出该依赖项目的 GUID。 这对应于**ProjectGuid**依赖项目文件中的元素。|  
|**ProjectPath**|所需**xs: string**属性。<br /><br /> 相对路径，包括的项目文件名称，有你想要包括的输出的相关项目。 此路径是相对于包含 SharePoint 项目项的 SharePoint 项目的根文件夹。|  
|**Target**|可选**xs: string**属性。<br /><br /> 若要在 SharePoint 服务器上，相对于部署根文件夹部署的依赖项目输出路径。 部署根文件夹由指定的部署类型**类型**属性。<br /><br /> 有关详细信息，请参阅说明**部署路径**和**部署根**属性的 SharePoint 项目中的项[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md).|  
|**类型**|所需**xs: string**属性。<br /><br /> 要用于该依赖项目的输出的部署类型。 有关可能的值的详细信息，请参阅的描述**部署类型**属性中的 SharePoint 项目项[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[文件](../sharepoint/files-element.md)|指定要包括在 SharePoint 项目项部署到 SharePoint 时的文件。|  
  
## <a name="remarks"></a>备注  
 使用**ProjectOutputFile**元素以在部署中的 SharePoint 项目项包含项目的输出。 你可以指定不同的项目或包含项目项的同一项目。 有关详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>元素信息  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|No|  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供打包和部署在项目项中的信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  