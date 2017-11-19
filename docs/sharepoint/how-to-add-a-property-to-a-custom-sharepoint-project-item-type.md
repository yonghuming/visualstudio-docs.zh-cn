---
title: "如何： 向自定义 SharePoint 项目项类型添加属性 |Microsoft 文档"
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
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c8971d6da08afa6140c049aa81937b0804cd363
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>如何：向自定义 SharePoint 项目项类型中添加属性
  当定义自定义的 SharePoint 项目项类型时，你可以将属性添加到项目项。 属性将显示在**属性**窗口中选择项目项**解决方案资源管理器**。  
  
 以下步骤假定你已定义你自己的 SharePoint 项目项类型。 有关详细信息，请参阅[如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>若要将属性添加到项目项类型的定义  
  
1.  定义具有表示要添加到自定义项目项类型的属性的公共属性的类。 如果你想要将多个属性添加到自定义项目项类型，你可以在同一类中或在不同的类定义所有属性。  
  
2.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>实现，句柄<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件*projectItemTypeDefinition*参数。  
  
3.  事件处理程序中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件，将你的自定义属性类的一个实例添加<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>事件自变量参数的集合。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何添加名为的属性**示例属性**向自定义项目项类型。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>了解代码  
 若要确保的同一个实例`CustomProperties`类每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件发生时，该代码示例将保存到的属性对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性发生此事件的项目项第一个时间。 再次发生此事件时，此代码将检索此对象。 有关使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性将数据保存借助项目项，请参阅[关联与 SharePoint 工具扩展的自定义数据](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 若要保留对属性值，更改**设置**访问器`ExampleProperty`将保存到的新值<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>与关联属性的对象。 有关使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性以保留数据与项目项，请参阅[扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>指定自定义属性的行为  
 你可以定义自定义属性显示的方式和在行为上与**属性**通过应用中的属性窗口<xref:System.ComponentModel>到属性定义的命名空间。 以下属性可在许多情况下：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>： 指定出现在属性的名称**属性**窗口。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>： 指定出现的描述字符串中的底部**属性**窗口时选择属性。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>： 指定的属性的默认值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>： 指定在显示的字符串之间的自定义转换**属性**窗口和非字符串属性值。  
  
-   <xref:System.ComponentModel.EditorAttribute>： 指定要用于修改属性的自定义编辑器。  
  
## <a name="compiling-the-code"></a>编译代码  
 这些代码示例需要引用以下程序集的类库项目：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>部署项目项  
 若要启用其他开发人员能够使用您的项目项，创建项目模板或项目项模板。 有关详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署的项目项，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集，该模板后和你想要随此项目项分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 定义 SharePoint 项目项类型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [如何： 将快捷菜单项添加到自定义 SharePoint 项目项类型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  