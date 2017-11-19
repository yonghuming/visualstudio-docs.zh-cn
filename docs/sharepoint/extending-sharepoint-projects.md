---
title: "扩展 SharePoint 项目 |Microsoft 文档"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0bbb086c66bad3ad2beedab2b390244a9e185b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-projects"></a>扩展 SharePoint 项目
  当你想要自定义 SharePoint 项目的项目级别功能，请创建一个项目扩展。 例如，你可以添加自定义项目属性中，或用户开发的 Visual Studio 中的 SharePoint 解决方案时引发的项目级事件做出响应。  
  
## <a name="creating-project-extensions"></a>创建项目扩展  
 若要扩展项目项，生成的 Visual Studio 扩展程序集实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>接口。 有关详细信息，请参阅[如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
 当你创建项目扩展时，你还可以向 SharePoint 项目中添加以下功能：  
  
-   添加快捷菜单项。 打开中的 SharePoint 项目节点的快捷菜单时显示的菜单项**解决方案资源管理器**通过右键单击节点或选择它，然后选择 Shift + F10 键。 有关详细信息，请参阅[如何： 将快捷菜单项添加到 SharePoint 项目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)。  
  
-   添加一个自定义属性。 属性将显示在**属性**窗口时选择中的 SharePoint 项目**解决方案资源管理器**。 有关详细信息，请参阅[如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 有关演示如何创建、 部署和测试项目扩展的演练，请参阅[演练： 创建 SharePoint 项目扩展](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)。  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>了解项目扩展和项目实例之间的关系  
 当你创建项目扩展时，该扩展加载任何类型的 SharePoint 项目中打开时[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包括多种 SharePoint 项目模板，例如列表定义、 内容类型和事件接收器。 但是，没有只有一个 SharePoint 项目类型。 出现在项目类型**新项目**对话框是仅将捆绑在一起的一个或多个 SharePoint 项目项的模板。 由于只有一个 SharePoint 项目类型，创建一个项目的扩展将应用于所有 SharePoint 项目。 例如，不能创建一个扩展，仅适用于**内容类型**项目。  
  
 若要访问的特定项目实例，处理之一<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>的事件*projectService*的实现中的参数<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法。 例如，若要确定 SharePoint 项目添加到解决方案时，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>事件。 有关详细信息，请参阅[如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何： 将快捷菜单项添加到 SharePoint 项目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [演练： 创建 SharePoint 项目扩展](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)   
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  