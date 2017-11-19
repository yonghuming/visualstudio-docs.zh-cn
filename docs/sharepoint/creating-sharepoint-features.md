---
title: "创建 SharePoint 功能 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
ms.assetid: 2e211fb3-94f4-4921-ba77-2ba6717a3e41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8f78a12aa70c3c7042a821a737485da963f7a56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-features"></a>创建 SharePoint 功能
  SharePoint 功能可用于更易于部署的相关的 SharePoint 项目项进行分组。 你可以创建功能、 设置作用域，并通过使用 SharePoint 功能设计器将其他功能标记为依赖关系。 设计器还会生成一个清单，这是一个 XML 文件，描述每个功能。  
  
## <a name="adding-features-to-the-sharepoint-solution"></a>将功能添加到 SharePoint 解决方案  
 通过使用解决方案资源管理器或打包资源管理器，可以向 SharePoint 解决方案中添加一项功能。 你可以使用以下方法之一添加一项功能。  
  
-   在**解决方案资源管理器**，打开快捷菜单**功能**，然后选择**添加功能**。  
  
-   在**打包资源管理器**，打开该包的快捷菜单，然后选择**添加功能**。  
  
## <a name="using-the-feature-designer"></a>使用功能设计器  
 SharePoint 解决方案可以包含一个或多个 SharePoint 功能，在解决方案资源管理器中的功能节点下分组。 每个功能都有自己**功能设计器**可用于自定义功能属性。 有关详细信息，请参阅[如何： 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)。 若要从另一个区分功能，可以配置的功能属性，如标题、 说明、 版本和作用域。  
  
### <a name="feature-designer-options"></a>功能设计器选项  
 创建一项功能后，你可以使用功能设计器自定义它。  
  
 下表介绍功能设计器中显示的功能属性。  
  
|属性|描述|  
|--------------|-----------------|  
|标题|可选。 该功能的默认标题设置为*SolutionName**FeatureName*。|  
|描述|可选。 SharePoint 功能的说明。|  
|范围|必需。 如果通过创建一项功能**解决方案资源管理器**，作用域默认设置为 Web。<br /><br /> -场： 激活的整个服务器场的功能。<br /><br /> 站点： 激活网站集中的所有 web 站点的功能。<br /><br /> -Web： 激活特定网站的功能。<br /><br /> -Web 应用程序： 激活某项功能的 web 应用中的所有 web 站点。|  
|解决方案中的项|可以添加到该功能的所有 SharePoint 项。|  
|功能中的项|已添加到功能 SharePoint 项目项。|  
  
## <a name="adding-and-removing-sharepoint-project-items"></a>添加和移除 SharePoint 项目项  
 你可以选择你想要添加到部署的 SharePoint 功能的 SharePoint 项目项。 使用**功能设计器**添加和移除项功能，以及查看功能清单。 有关详细信息，请参阅[如何： 添加和移除项 SharePoint 功能](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)。  
  
## <a name="adding-feature-dependencies"></a>添加功能依赖关系  
 你可以配置的功能清单，以便 SharePoint 服务器激活某些功能之前激活你的功能。 例如，如果你的 SharePoint 功能依赖于用于功能或数据的其他功能，SharePoint 服务器可以首先尝试激活任何取决于你的功能的功能。 有关详细信息，请参阅[如何： 添加和移除功能依赖关系](../sharepoint/how-to-add-and-remove-feature-dependencies.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 自定义 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [如何： 添加和移除项 SharePoint 功能](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [如何：添加和删除功能依赖项](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  