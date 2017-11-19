---
title: "如何： 向 SharePoint 项目中添加属性 |Microsoft 文档"
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
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e43e4921a32cc84b8384950e88c589b1bbddc31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>如何：向 SharePoint 项目中添加属性
  项目扩展可用于将属性添加到任何 SharePoint 项目。 属性将显示在**属性**窗口中选定项目**解决方案资源管理器**。  
  
 以下步骤假定你已创建了一个项目扩展。 有关详细信息，请参阅[如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>若要将属性添加到 SharePoint 项目  
  
1.  定义具有表示要添加到 SharePoint 项目的属性的公共属性的类。 如果你想要添加多个属性，你可以在同一类中或在不同的类定义所有属性。  
  
2.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>实现，句柄<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件*projectService*参数。  
  
3.  事件处理程序中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件，将你的属性类的一个实例添加<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>事件自变量参数的集合。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何将两个属性添加到 SharePoint 项目。 一个属性仍然存在自身的数据项目用户选项文件 (。 csproj.user 文件或。 vbproj.user 文件)。 其他属性保持其数据的项目文件 （.csproj 文件或.vbproj 文件） 中。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>了解代码  
 若要确保的同一个实例`CustomProjectProperties`类每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件发生时，代码示例将添加到的属性对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>项目第一个时间发生此事件的属性。 再次发生此事件时，此代码将检索此对象。 有关使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>属性以将数据与项目中，请参阅[关联与 SharePoint 工具扩展的自定义数据](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 若要保留对属性值，更改**设置**属性访问器使用以下 Api:  
  
-   `CustomUserFileProperty`使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>属性将其值保存到项目用户选项文件。  
  
-   `CustomProjectFileProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法将其值保存到项目文件。  
  
 有关这些文件中的持久保存数据的详细信息，请参阅[扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>指定自定义属性的行为  
 你可以定义自定义属性显示的方式和在行为上与**属性**通过应用中的属性窗口<xref:System.ComponentModel>到属性定义的命名空间。 以下属性可在许多情况下：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>： 指定出现在属性的名称**属性**窗口。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>： 指定出现的描述字符串中的底部**属性**窗口时选择属性。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>： 指定的属性的默认值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>： 指定在显示的字符串之间的自定义转换**属性**窗口和非字符串属性值。  
  
-   <xref:System.ComponentModel.EditorAttribute>： 指定要用于修改属性的自定义编辑器。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目](../sharepoint/extending-sharepoint-projects.md)   
 [如何： 创建 SharePoint 项目扩展](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何： 将快捷菜单项添加到 SharePoint 项目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  