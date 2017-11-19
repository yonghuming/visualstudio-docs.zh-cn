---
title: "SafeControl 元素 |Microsoft 文档"
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
helpviewer_keywords: SafeControl element
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d9651c320e574c8db9fcafcb6e98f13e45eac1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="safecontrol-element"></a>SafeControl 元素
  表示一个 ASPX 控件或指定为安全的任何用户访问 SharePoint 站点上的任意 ASPX 页上的 Web 部件。  
  
## <a name="syntax"></a>语法  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**Assembly**|可选**xs: string**属性。<br /><br /> 定义的 ASPX 控件或 Web 部件的程序集的名称。 默认情况下，此属性使用**$SharePoint.Project.AssemblyFullName$**为程序集名称的可替换参数。 有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。|  
|**IsSafe**|可选**xs: boolean**属性。<br /><br /> 指定是否允许不受信任的用户访问安全的 ASPX 控件或 Web 部件。|  
|**IsSafeAgainstScript**|可选**xs: boolean**属性。<br /><br /> 指定不受信任的用户是否可以查看或编辑的 ASPX 控件或 Web 部件的属性。|  
|**Name**|可选**xs: string**属性。<br /><br /> 此集合中的安全控件项的名称。|  
|**Namespace**|可选**xs: string**属性。<br /><br /> Web 部件的 ASPX 控件命名空间。|  
|**类型名称**|可选**xs: string**属性。<br /><br /> Web 部件的 ASPX 控件的类型名称。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示 ASPX 控件和指定为安全的任何用户访问 SharePoint 站点上的任意 ASPX 页上的 Web 部件的集合。|  
  
## <a name="remarks"></a>备注  
 安全控件有关的详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>元素信息  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|No|  
  
## <a name="see-also"></a>另请参阅  
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  