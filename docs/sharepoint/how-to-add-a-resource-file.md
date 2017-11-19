---
title: "如何： 将一个资源文件 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7233bc1a739bd3bf6544aad879f898bf3848ee7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-resource-file"></a>如何：添加资源文件
  有关将资源文件添加的命令是解决方案节点和在解决方案资源管理器的功能节点的快捷菜单上。 有关详细信息，请参阅[本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>若要将全局资源文件添加到 SharePoint 解决方案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，打开 SharePoint 解决方案。  
  
2.  在**解决方案资源管理器**，选择 SharePoint 项目节点，然后，在菜单栏上，选择**项目**，**添加新项**。  
  
3.  在**添加新项**对话框框中，选择**全局资源文件**模板，然后选择**添加**按钮。  
  
    > [!NOTE]  
    >  仅当选择 SharePoint 项目项时，将显示全局资源文件的项目项模板。  
  
4.  在**添加资源**对话框框中，选择资源文件，例如英语 （美国） 区域性。  
  
     此步骤将全局资源文件添加到你的解决方案中的格式，资源*x***。***区域性***。**resx，如 Resource1.en US.resx。  
  
5.  当**资源编辑器**在中打开[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，将资源添加到资源文件。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>若要将功能资源文件添加到 SharePoint 功能  
  
1.  如果尚未在中打开 SharePoint 解决方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，打开解决方案。  
  
2.  在**解决方案资源管理器**，打开下的功能的名称的快捷菜单**功能**节点，然后选择**添加功能资源**。  
  
     此步骤将资源文件添加到在格式中，功能*ResourceFileName***。***区域性***。**resx，如 Feature1.en US.resx。  
  
3.  当**资源编辑器**在中打开[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，将资源添加到资源文件。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  