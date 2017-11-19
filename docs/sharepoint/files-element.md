---
title: "文件元素 |Microsoft 文档"
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
helpviewer_keywords: Files element
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dcb3e7e81d9897f23742eda83c72bb64caed65da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="files-element"></a>Files 元素
  指定要部署使用 SharePoint 项目项，如功能元素文件和依赖的非 SharePoint 项目的输出的文件。  
  
## <a name="syntax"></a>语法  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>类型  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|可选**ProjectItemFileType**元素。<br /><br /> 表示 SharePoint 文件，如功能元素文件中，要包括在项目项部署到 SharePoint 时。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|可选**ProjectOutputFileType**元素。<br /><br /> 表示要部署到 SharePoint 项目项包含项目的输出。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[项目项](../sharepoint/projectitem-element.md)|表示一个 SharePoint 项目项。 这是.spdata 文件的所需的根元素。|  
  
## <a name="element-information"></a>元素信息  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|No|  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  