---
title: "如何： 向 SharePoint 项目项扩展中添加属性 |Microsoft 文档"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51b75626a76778c5f00ed9408950f999133209dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>如何：向 SharePoint 项目项扩展中添加属性
  项目项扩展可用于将属性添加到任何已安装在 Visual Studio 中的 SharePoint 项目项。 属性将显示在**属性**窗口中选择项目项**解决方案资源管理器**。  
  
 以下步骤假定你已创建了项目项扩展。 有关详细信息，请参阅[如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>若要将属性添加到项目项扩展  
  
1.  定义具有表示要添加到项目项类型的属性的公共属性的类。 如果你想要将多个属性添加到项目项类型，你可以在同一类中或在不同的类定义所有属性。  
  
2.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>实现，句柄<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件*projectItemType*参数。  
  
3.  事件处理程序中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件，将你的属性类的一个实例添加<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>事件自变量参数的集合。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何添加名为的属性**示例属性**到事件接收器项目项。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>了解代码  
 若要确保的同一个实例`CustomProperties`类每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件发生时，代码示例将添加到的属性对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性发生此事件的项目项第一个时间。 再次发生此事件时，此代码将检索此对象。 有关使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性以将数据与项目项关联请参阅[关联与 SharePoint 工具扩展的自定义数据](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 若要保留对属性值，更改**设置**访问器`ExampleProperty`将保存到的新值<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>与关联属性的对象。 有关使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性以保留数据与项目项，请参阅[扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>指定自定义属性的行为  
 你可以定义自定义属性显示的方式和在行为上与**属性**通过应用中的属性窗口<xref:System.ComponentModel>到属性定义的命名空间。 以下属性可在许多情况下：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>： 指定出现在属性的名称**属性**窗口。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>： 指定出现的描述字符串中的底部**属性**窗口时选择属性。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>： 指定的属性的默认值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>： 指定在显示的字符串之间的自定义转换**属性**窗口和非字符串属性值。  
  
-   <xref:System.ComponentModel.EditorAttribute>： 指定要用于修改属性的自定义编辑器。  
  
## <a name="compiling-the-code"></a>编译代码  
 这些示例需要引用以下程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建 SharePoint 项目项扩展](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 向 SharePoint 项目项扩展中添加快捷菜单项](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)   
 [演练：扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  