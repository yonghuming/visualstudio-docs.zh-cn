---
title: "如何： 将快捷菜单项添加到 SharePoint 项目项扩展 |Microsoft 文档"
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
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c3cb29fa90917f50b42579bf6f274aa8a20d99f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>如何：向 SharePoint 项目项扩展中添加快捷菜单项
  你可以通过使用项目项扩展添加到现有 SharePoint 项目项的快捷菜单项。 菜单项显示在用户右键单击中的项目项时**解决方案资源管理器**。  
  
 以下步骤假定你已创建了项目项扩展。 有关详细信息，请参阅[如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>若要在项目项扩展中添加快捷菜单项  
  
1.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>实现，句柄<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件*projectItemType*参数。  
  
2.  你的事件处理程序中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件，添加新<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>对象传递给<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>或<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>事件自变量参数的集合。  
  
3.  在<xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新的事件处理程序<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>对象，执行你想要在用户单击快捷菜单项时执行的任务。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何将快捷菜单项添加到事件接收器项目项。 当用户右键单击中的项目项**解决方案资源管理器**并单击**编写消息发送到输出窗口**菜单项，Visual Studio 显示一条消息中的**输出**窗口。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 此示例使用 SharePoint 项目服务要写入到消息**输出**窗口。 有关详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 向 SharePoint 项目项扩展中添加属性](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)   
 [演练：扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  