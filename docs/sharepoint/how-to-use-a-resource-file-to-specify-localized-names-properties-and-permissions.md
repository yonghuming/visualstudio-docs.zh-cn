---
title: "如何： 使用资源文件来指定本地化的名称、 属性和权限 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a8b61477ae3b588b2aeadf1c9d99618151825f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>如何：使用资源文件指定本地化名称、属性和权限
  通过使用资源文件，您可以对在业务数据连接 (BDC) 模型中定义的对象提供本地化名称、定义属性和应用权限。 若要指定此信息，你添加**业务数据连接资源**项包含的项目**业务数据连接模型**项。 然后通过编辑资源文件的 XML 来指定名称、属性和权限。  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>将 BDC 资源文件添加到 SharePoint 项目  
  
1.  在**解决方案资源管理器**，展开 SharePoint 项目的文件夹，然后选择包含 BDC 模型的文件夹。  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在**添加新项**对话框框中，选择**业务数据连接资源项**。  
  
5.  在**名称**框中，指定资源文件的名称，然后选择**添加**按钮。  
  
     扩展名为 .bdcr 的资源文件将添加到项目中并打开以进行编辑。  
  
6.  添加 XML 以定义要应用 BDC 模型的本地化名称、属性和权限。  
  
     有关如何定义这些元素的信息，请参阅[模型和资源文件](http://go.microsoft.com/fwlink/?LinkID=169283)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 向 SharePoint 项目中添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 在 BDC 功能中包含自定义程序集](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  