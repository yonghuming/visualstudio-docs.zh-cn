---
title: "如何： 将快捷菜单项添加到自定义 SharePoint 项目项类型 |Microsoft 文档"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0e8bdf4e0104b1358085107ffabb5d0c05d5924
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>如何：向自定义 SharePoint 项目项类型中添加快捷菜单项
  当定义自定义的 SharePoint 项目项类型时，你可以将快捷菜单项添加到项目项。 菜单项显示在用户右键单击中的项目项时**解决方案资源管理器**。  
  
 以下步骤假定你已定义你自己的 SharePoint 项目项类型。 有关详细信息，请参阅[如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>将快捷菜单项添加到自定义项目项类型  
  
1.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>实现，句柄<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件*projectItemTypeDefinition*参数。  
  
2.  你的事件处理程序中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件，添加新<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>对象传递给<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>或<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>事件自变量参数的集合。  
  
3.  在<xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新的事件处理程序<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>对象，执行你想要在用户选择快捷菜单项时执行的任务。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何将上下文菜单项添加到自定义项目项类型。 当用户从项目项打开快捷菜单**解决方案资源管理器**并选择**编写消息发送到输出窗口**菜单项，Visual Studio 显示一条消息中的**输出**窗口。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 此示例使用 SharePoint 项目服务要写入到消息**输出**窗口。 有关详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>部署项目项  
 若要启用其他开发人员能够使用您的项目项，创建项目模板或项目项模板。 有关详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署的项目项，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集，该模板后和你想要随此项目项分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [如何： 向自定义 SharePoint 项目项类型添加属性](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  