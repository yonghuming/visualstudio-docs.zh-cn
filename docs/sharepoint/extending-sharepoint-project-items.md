---
title: "扩展 SharePoint 项目项 |Microsoft 文档"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f17e43e2fe98e36939c91b37e72b185cb14d09e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-project-items"></a>扩展 SharePoint 项目项
  当你想要将功能添加到已安装在 Visual Studio 中的 SharePoint 项目项类型时，请创建项目项扩展。 例如，你可以创建为内置的扩展**事件接收器**或**列表定义**项目项在 Visual Studio 中，或可以创建自定义项目项类型的扩展。 你还可以创建的 SharePoint 项目项的所有类型的扩展。  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>用于扩展 SharePoint 项目项的任务  
 若要扩展项目项，生成的 Visual Studio 扩展程序集实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>接口。 有关详细信息，请参阅[如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
 扩展项目项时，你还可以向项目项中添加以下功能：  
  
-   将快捷菜单项添加到项目项。 打开中的项目项的快捷菜单时显示的菜单项**解决方案资源管理器**。 通过右击项目项打开快捷菜单或通过选择它，然后选择 Shift + F10 键。 有关详细信息，请参阅[如何： 向 SharePoint 项目项扩展中添加快捷菜单项](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)。  
  
-   将自定义属性添加到项目项。 属性将显示在**属性**窗口时选择中的项目项**解决方案资源管理器**。 有关详细信息，请参阅[如何： 向 SharePoint 项目项扩展中添加属性](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)。  
  
 有关演示如何创建、 部署和测试项目项扩展的演练，请参阅[演练： 扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>了解项目项扩展和项目项实例之间的关系  
 在创建项目项扩展时，Visual Studio 将加载你的扩展关联的类型的项目项添加到 SharePoint 项目时。 例如，如果你创建的扩展**事件接收器**项目项，当用户将添加 Visual Studio 加载您的扩展**事件接收器**项目项的项目。 Visual Studio 将使用你的扩展的同一个实例关联的项目项类型的所有实例。 在上一示例中，如果用户将添加第二个**事件接收器**项项目到项目中，你的扩展的同一个实例用于自定义第二个项目项。  
  
 若要访问所扩展的项目项类型的特定实例，处理之一<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>的事件*projectItemType*的实现中的参数<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法。 例如，若要确定所扩展的类型的项目项添加到项目时，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>事件。 有关详细信息，请参阅[如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint 项目项的标识符  
 每个 SharePoint 项目项都有相应的字符串标识符。 如果你想要执行以下任务，你必须知道项目项的标识符：  
  
-   创建项目项的扩展。 在这种情况下，必须将你想要扩展的构造函数的项目项的标识符传递<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 若要为所有项目项类型创建的扩展，将传递 **\*** 字符串值。  
  
-   以编程方式添加到项目的项目项。 在这种情况下，必须传递到的项目项的标识符<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>方法。  
  
 下表列出的 Visual Studio 附带的 SharePoint 项目项的标识符。  
  
|项目项名称|字符串标识符|  
|-----------------------|-----------------------|  
|业务数据目录模型|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|内容类型|Microsoft.VisualStudio.SharePoint.ContentType|  
|事件接收器|Microsoft.VisualStudio.SharePoint.EventHandler|  
|空元素|Microsoft.VisualStudio.SharePoint.GenericElement|  
|列表定义<br /><br /> 从内容类型的列表定义|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|列表实例|Microsoft.VisualStudio.SharePoint.ListInstance|  
|模块|Microsoft.VisualStudio.SharePoint.Module|  
|顺序工作流<br /><br /> 状态机工作流|Microsoft.VisualStudio.SharePoint.Workflow|  
|站点定义|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|可视 Web 部件|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web 部件|Microsoft.VisualStudio.SharePoint.WebPart|  
|工作流关联窗体|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 向 SharePoint 项目项扩展中添加快捷菜单项](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [如何： 向 SharePoint 项目项扩展中添加属性](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [演练： 扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)  
  